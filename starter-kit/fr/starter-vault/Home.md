
```dataviewjs
// Détection dynamique du dossier parent (fonctionne à la racine OU dans un sous-dossier)
const currentFolder = dv.current().file.folder;
const prefix = currentFolder ? currentFolder + "/" : "";

const now = new Date();
const currentYear = now.getFullYear();
const currentYearMonth = `${currentYear}-${String(now.getMonth() + 1).padStart(2, '0')}`;

// 1. Charger tous les Domaines de Vie (fiches canoniques)
const areas = dv.pages(`"${prefix}3-Domaines-de-vie"`)
    .where(p => p.file.name !== "README");

// 2. Charger les Projets Actifs dans 1-Projects
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
    ? "⚠️ **Attention à la dispersion mensuelle** (Recommandation : 2 à 4 domaines sous focus chaud par mois)" 
    : "🟢 **Focus Mensuel Optimal** (Canalisation idéale de la charge de travail)";

let hotStr = hotAreas.map(a => {
    let hotPart = a.hotProjects.map(p => p.file.link).join(" · ");
    let standbyPart = a.standbyProjects.length > 0 ? ` *(🟡 Stand-by : ${a.standbyProjects.map(p => p.file.link).join(" · ")})*` : "";
    return `> - **🔥 ${a.link}** ➔ ${hotPart}${standbyPart}`;
}).join("\n");

let standbyStr = standbyAreas.map(a => `> - **🟡 ${a.link}** ➔ ` + a.standbyProjects.map(p => p.file.link).join(" · ")).join("\n");
let dormantStr = dormantAreas.map(a => a).join(" · ");

dv.paragraph(`> [!tip] **Focus mois courant : ${totalHotAreas} domaines actifs (${ratio}%)**\n> ${statusMsg}\n>\n` +
`> **🔥 ${totalHotAreas} Domaines avec un focus (${allHotProjects.size} projets sur le mois courant) :**\n` + (hotStr || "> *Aucun*") + `\n>\n` +
`> **🟡 ${standbyAreas.length} Domaines en stand-by cette année (${allStandbyProjects.size} projets au repos) :**\n` + (standbyStr || "> *Aucun*") + `\n>\n` +
`> **💤 ${dormantAreas.length} Domaines en repos / friche saisonnière :** ` + (dormantStr || "*Aucun*")
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

dv.paragraph(`> [!rocket] 🚀 **Métriques de Productivité & Effet Levier IA**\n` +
`> - ⚡ **Vitesse & Levier IA :** **x${totalSpeed}** *(Gain net : **+${formatHours(totalGainH)}** · **${totalPct}%** de temps économisé)*\n` +
`> - ⏱️ **Volume Deep Work Cumulé :** **${formatHours(totalRealHours)} réelles** *(Équivalent sans IA : ~${formatHours(totalSansIaHours)})*\n` +
`> - 🪵 **Engagement Système :** **${totalSessions} sessions** enregistrées`
);
```

> [!stats] 📈 Activité du Cerveau
> - **Toutes les Notes :** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '"').length` | **Inbox :** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '0-Inbox"').length` | **Distillées :** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '2-Ressources/IA-generated"').length` | **Thèmes :** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '2-Ressources/Themes"').length` | **Archives :** `$= const p = dv.current().file.folder ? dv.current().file.folder + '/' : ''; dv.pages('"' + p + '4-Archives/Projets"').length`
> 
> **Outils OS :** [[_Arca-BrainOS/log|📜 Journal Système]] | [[0-Inbox/|📥 Accéder à l'Inbox]] | [[3-Domaines-de-vie/README|🧠 Domaines de Vie]]
