```dataviewjs
// Dynamic folder detection (works at vault root OR inside sub-folders)
const currentFolder = dv.current().file.folder;
const prefix = currentFolder ? currentFolder + "/" : "";

const now = new Date();
const currentYear = now.getFullYear();
const currentYearMonth = `${currentYear}-${String(now.getMonth() + 1).padStart(2, '0')}`;

// 1. Load all Life Areas
const areas = dv.pages(`"${prefix}3-Domaines-de-vie"`)
    .where(p => p.file.name !== "README");

// 2. Load Active Projects in 1-Projects
const activeProjects = dv.pages(`"${prefix}1-Projects"`)
    .where(p => (p.file.name.startsWith("P-") || p.category === "Projet") 
             && p.status !== "completed" 
             && p.status !== "paused" 
             && !p.tags?.includes("statut/termine"));

function getProjectDateStr(p) {
    if (p.last_session && String(p.last_session).trim() !== "") {
        let d = String(p.last_session).trim();
        if (d.length >= 7) return d.substring(0, 10);
    }
    if (p.date_created && String(p.date_created).trim() !== "") {
        let d = String(p.date_created).trim();
        if (d.length >= 7) return d.substring(0, 10);
    }
    return "";
}

let hotAreas = [];      
let standbyAreas = [];  
let dormantAreas = [];  

let allHotProjects = new Set();
let allStandbyProjects = new Set();

for (let area of areas) {
    let areaName = area.file.name;
    
    let matchingProjects = activeProjects.where(p => {
        if (!p.areas) return false;
        let areaList = Array.isArray(p.areas) ? p.areas : [p.areas];
        return areaList.some(a => {
            let str = typeof a === "string" ? a : (a && a.path ? a.path : (a && a.fileName ? a.fileName : String(a)));
            return str.includes(areaName);
        });
    });
    
    if (matchingProjects.length === 0) {
        dormantAreas.push(area.file.link);
        continue;
    }
    
    let hotProjects = [];
    let standbyProjects = [];
    
    for (let p of matchingProjects) {
        let dateStr = getProjectDateStr(p);
        if (dateStr.startsWith(currentYearMonth)) {
            hotProjects.push(p);
            allHotProjects.add(p.file.name);
        } else {
            standbyProjects.push(p);
            allStandbyProjects.add(p.file.name);
        }
    }
    
    if (hotProjects.length > 0) {
        hotAreas.push({ link: area.file.link, hotProjects: hotProjects, standbyProjects: standbyProjects });
    } else if (standbyProjects.length > 0) {
        standbyAreas.push({ link: area.file.link, standbyProjects: standbyProjects });
    } else {
        dormantAreas.push(area.file.link);
    }
}

let totalHotAreas = hotAreas.length;
let ratio = areas.length > 0 ? Math.round((totalHotAreas / areas.length) * 100) : 0;

let statusMsg = totalHotAreas > 4 
    ? "⚠️ **Attention to monthly dispersion** (Recommended: 2 to 4 active focus areas per month)" 
    : "🟢 **Optimal Monthly Focus** (Ideal workload alignment)";

let hotStr = hotAreas.map(a => {
    let hotPart = a.hotProjects.map(p => p.file.link).join(" · ");
    let standbyPart = a.standbyProjects.length > 0 ? ` *(🟡 Stand-by: ${a.standbyProjects.map(p => p.file.link).join(" · ")})*` : "";
    return `> - **🔥 ${a.link}** ➔ ${hotPart}${standbyPart}`;
}).join("\n");

let standbyStr = standbyAreas.map(a => `> - **🟡 ${a.link}** ➔ ` + a.standbyProjects.map(p => p.file.link).join(" · ")).join("\n");
let dormantStr = dormantAreas.map(a => a).join(" · ");

dv.paragraph(`> [!tip] **Current Month Focus: ${totalHotAreas} Active Areas (${ratio}%)**\n> ${statusMsg}\n>\n` +
`> **🔥 ${totalHotAreas} Focus Areas (${allHotProjects.size} current month projects):**\n` + (hotStr || "> *None*") + `\n>\n` +
`> **🟡 ${standbyAreas.length} Stand-by Areas (${allStandbyProjects.size} dormant projects):**\n` + (standbyStr || "> *None*") + `\n>\n` +
`> **💤 ${dormantAreas.length} Resting Areas:** ` + (dormantStr || "*None*")
);
```

```dataviewjs
const currentFolder = dv.current().file.folder;
const prefix = currentFolder ? currentFolder + "/" : "";

function parseHours(str) {
    if (!str) return 0;
    let s = String(str).trim();
    let m = s.match(/(\d+)h(\d+)?/);
    if (!m) return parseFloat(s) || 0;
    let h = parseInt(m[1], 10) || 0;
    let min = parseInt(m[2], 10) || 0;
    return h + (min / 60);
}

function formatHours(hours) {
    let h = Math.floor(hours);
    let m = Math.round((hours - h) * 60);
    if (m === 60) { h += 1; m = 0; }
    return `${h}h${String(m).padStart(2, '0')}`;
}

const allProjects = dv.pages(`"${prefix}1-Projects"`).concat(dv.pages(`"${prefix}4-Archives/Projets"`));

let totalSessions = 0, totalRealHours = 0, totalSansIaHours = 0;

for (let p of allProjects) {
    let sess = parseInt(p.sessions_count, 10) || 0;
    let realH = parseHours(p.total_real_duration || p.duree_cumulee_reelle);
    let sansIaH = parseHours(p.total_estimated_manual || p.duree_cumulee_sans_ia);
    
    totalSessions += sess;
    totalRealHours += realH;
    totalSansIaHours += sansIaH;
}

let totalGainH = Math.max(0, totalSansIaHours - totalRealHours);
let totalSpeed = totalRealHours > 0 ? (totalSansIaHours / totalRealHours).toFixed(2) : "1.00";
let totalPct = totalSansIaHours > 0 ? ((totalGainH / totalSansIaHours) * 100).toFixed(1) : "0.0";

dv.paragraph(`> [!rocket] 🚀 **Productivity Metrics & AI Leverage**\n` +
`> - ⚡ **Speed & AI Leverage:** **x${totalSpeed}** *(Net Gain: **+${formatHours(totalGainH)}** · **${totalPct}%** time saved)*\n` +
`> - ⏱️ **Cumulated Deep Work:** **${formatHours(totalRealHours)} real hours** *(Without AI equivalent: ~${formatHours(totalSansIaHours)})*\n` +
`> - 🪵 **System Engagement:** **${totalSessions} sessions** logged`
);
```

> [!stats] 📈 Brain Telemetry
> - **All Notes:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '"').length` | **Inbox:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '0-Inbox"').length` | **AI Distilled:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '2-Ressources/IA-generated"').length` | **Themes:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '2-Ressources/Themes"').length` | **Archives:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '4-Archives/Projets"').length`
> 
> **OS Tools:** [[_Arca-BrainOS/log|📜 System Worklog]] | [[0-Inbox/|📥 Open Inbox]] | [[3-Domaines-de-vie/README|🧠 Life Areas]]
