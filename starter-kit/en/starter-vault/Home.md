
# Home page
```dataviewjs
// Dynamic folder detection (works at vault root OR inside sub-folders)
const currentFolder = dv.current().file.folder;
const prefix = currentFolder ? currentFolder + "/" : "";

const now = new Date();
const THIRTY_DAYS_MS = 30 * 24 * 60 * 60 * 1000;

// 1. Load all Life Areas (canonical notes)
const areas = dv.pages(`"${prefix}3-Domaines-de-vie"`)
    .where(p => p.file.name !== "2026" && p.file.name !== "Cartographie-processus-de-vie" && p.file.name !== "Life-process-mapping" && p.file.name !== "README");

// 2. Load Active Projects in 1-Projects
const activeProjects = dv.pages(`"${prefix}1-Projects"`)
    .where(p => (p.file.name.startsWith("P-") || p.category === "Projet" || p.category === "Project") 
             && p.status !== "completed" 
             && p.status !== "paused" 
             && !p.tags?.includes("statut/termine")
             && !p.tags?.includes("status/completed"));

function cleanAreaName(a) {
    if (!a) return "";
    let str = typeof a === "string" ? a : (a && a.path ? a.path : (a && a.fileName ? a.fileName : String(a)));
    return str.replace(/\[\[|\]\]/g, "").replace(/^.*3-Domaines-de-vie\//, "").replace(/\.md$/, "").trim();
}

function getProjectAreas(p) {
    if (!p.areas) return [];
    let list = Array.isArray(p.areas) ? p.areas : [p.areas];
    return list.map(cleanAreaName).filter(Boolean);
}

function getProjectDateStr(p) {
    let val = p.last_session || p.derniere_session || p.date_created || p["date-created"];
    if (!val) return "";
    if (typeof val === "object" && val.toISODate) return val.toISODate();
    if (typeof val === "object" && val.ts) {
        let d = new Date(val.ts);
        return d.toISOString().substring(0, 10);
    }
    let s = String(val).trim();
    if (s.length >= 10) return s.substring(0, 10);
    if (s.length >= 7) return s.substring(0, 7);
    return s;
}

function isProjectHot(p) {
    let dateStr = getProjectDateStr(p);
    if (!dateStr || dateStr.length < 10) return false;
    let d = new Date(dateStr);
    if (isNaN(d.getTime())) return false;
    let diff = now.getTime() - d.getTime();
    // Active if session is within the last 30 days (+1d timezone tolerance)
    return diff >= -86400000 && diff <= THIRTY_DAYS_MS;
}

let hotAreas = [];      
let standbyAreas = [];  
let dormantAreas = [];  

let allHotProjects = new Set();
let allStandbyProjects = new Set();

for (let p of activeProjects) {
    if (isProjectHot(p)) {
        allHotProjects.add(p.file.name);
    } else {
        allStandbyProjects.add(p.file.name);
    }
}

for (let area of areas) {
    let areaName = cleanAreaName(area.file.name);
    
    // Projects where this is the primary area (areas[0])
    let primaryProjects = activeProjects.filter(p => {
        let pAreas = getProjectAreas(p);
        return pAreas.length > 0 && pAreas[0] === areaName;
    });
    
    // Projects where this is a related / secondary area (areas[1..n])
    let secondaryProjects = activeProjects.filter(p => {
        let pAreas = getProjectAreas(p);
        return pAreas.length > 1 && pAreas.slice(1).includes(areaName);
    });
    
    let hotPrimary = primaryProjects.filter(p => isProjectHot(p));
    let standbyPrimary = primaryProjects.filter(p => !isProjectHot(p));
    let hotSecondary = secondaryProjects.filter(p => isProjectHot(p));
    let standbySecondary = secondaryProjects.filter(p => !isProjectHot(p));
    
    if (hotPrimary.length > 0) {
        hotAreas.push({
            link: area.file.link,
            hotPrimary: hotPrimary,
            hotSecondary: hotSecondary,
            standbyPrimary: standbyPrimary,
            standbySecondary: standbySecondary
        });
    } else if (standbyPrimary.length > 0 || hotSecondary.length > 0 || standbySecondary.length > 0) {
        standbyAreas.push({
            link: area.file.link,
            standbyPrimary: standbyPrimary,
            hotSecondary: hotSecondary,
            standbySecondary: standbySecondary
        });
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
    let parts = [];
    if (a.hotPrimary.length > 0) {
        parts.push(a.hotPrimary.map(p => p.file.link).join(" · "));
    }
    if (a.hotSecondary.length > 0) {
        parts.push(`*(related: ${a.hotSecondary.map(p => p.file.link).join(" · ")})*`);
    }
    if (a.standbyPrimary.length > 0 || a.standbySecondary.length > 0) {
        let sbList = [
            ...a.standbyPrimary.map(p => p.file.link),
            ...a.standbySecondary.map(p => `(${p.file.link})`)
        ];
        parts.push(`*(🟡 Stand-by: ${sbList.join(" · ")})*`);
    }
    return `> - **🔥 ${a.link}** ➔ ${parts.join(" ")}`;
}).join("\n");

let standbyStr = standbyAreas.map(a => {
    let parts = [];
    if (a.standbyPrimary.length > 0) {
        parts.push(a.standbyPrimary.map(p => p.file.link).join(" · "));
    }
    let allSecondary = [...a.hotSecondary, ...a.standbySecondary];
    if (allSecondary.length > 0) {
        parts.push(`*(related: ${allSecondary.map(p => p.file.link).join(" · ")})*`);
    }
    return `> - **🟡 ${a.link}** ➔ ${parts.join(" ")}`;
}).join("\n");

let dormantStr = dormantAreas.map(a => a).join(" · ");

dv.paragraph(`> [!tip] **Active Focus (rolling 30 days): ${totalHotAreas} Active Areas (${ratio}%)**\n> ${statusMsg}\n>\n` +
`> **🔥 ${totalHotAreas} Focus Areas (${allHotProjects.size} active projects in the last 30 days):**\n` + (hotStr || "> *None*") + `\n>\n` +
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

> [!stats] 📈 Vault Activity & Health
> - ⚡ **Active Work:** **Inbox:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '0-Inbox"').length` | **Active Projects:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '1-Projects"').where(p => (p.file.name.startsWith("P-") || p.category === "Projet" || p.category === "Project") && p.status !== "completed" && !p.tags?.includes("statut/termine") && !p.tags?.includes("status/completed")).length` | **Areas:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '3-Domaines-de-vie"').where(p => p.file.name !== "2026" && p.file.name !== "Cartographie-processus-de-vie" && p.file.name !== "Life-process-mapping" && p.file.name !== "README").length`
> - 🏛️ **Capitalized Knowledge:** **Themes:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '2-Ressources/Themes"').where(p => p.file.name.startsWith("T-")).length` | **AI Distillations:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '2-Ressources/IA-generated"').length` | **Archives:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '4-Archives/Projets"').length`
> - 🌐 **Global Volume:** **Total Notes:** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '"').length`
> 
> **OS Tools:** [[_Arca-BrainOS/log|📜 System Worklog]] | [[0-Inbox/|📥 Open Inbox]] | [[3-Domaines-de-vie/README|🧠 Life Areas]]

