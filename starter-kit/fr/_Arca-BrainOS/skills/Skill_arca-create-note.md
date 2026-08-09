---
name: arca-create-note
description: Instancier rapidement une nouvelle note Projet (P-), Thème (T-) ou Domaine de vie (Area) avec son template, son frontmatter et son maillage automatique.
---

# 🛠️ Skill : arca-create-note (Création & Initialisation de Note Structurée)

## Déclencheurs & Alias Spécifiques

Ce skill est déclenché par l'une des commandes ou alias suivants :

| Commande Directe / Alias | Action Immédiate Exécutée |
| :--- | :--- |
| `create-project`, `create-projet`, `arca-create-project`, `brain-create-project` | 🚀 Instancie un **Projet (`P-`)** dans `PATH_PROJECTS` |
| `create-theme`, `arca-create-theme`, `brain-create-theme` | 📜 Instancie un **Thème (`T-`)** dans `PATH_THEMES` |
| `create-domaine`, `create-area`, `arca-create-area`, `brain-create-area` | 🧠 Instancie un **Domaine de Vie** dans `PATH_AREAS` |
| `create-note`, `arca-create-note`, `brain-create-note` | ❓ **Mode Interactif** (Demande quel type de note créer) |

---

## Workflow d'Exécution Séquentiel

### 1. Routage selon l'Alias Invoqué :
- **Si l'alias est spécifique** (ex: `create-project` ou `create-theme`) ➔ Sauter l'étape de qualification et exécuter directement la branche ciblée.
- **Si la commande est générique** (`create-note`) ➔ Demander à l'utilisateur : *"Quel type de note souhaites-tu créer : 1. Projet (`P-`), 2. Thème (`T-`), ou 3. Domaine de Vie ?"*

---

### 2. Branche A : Création d'un Projet (`P-[Nom-Projet].md`) :
1. **Sollicitation des Métadonnées :**
   Demander au besoin :
   - Titre du projet (ex: `P-Mon-Nouveau-Projet`).
   - Domaine(s) de vie rattaché(s) (`areas: ["[[Nom-Domaine]]"]`).
   - Thème(s) rattaché(s) (`themes: ["[[T-Nom-Theme]]"]`).
2. **Génération du Fichier dans `PATH_PROJECTS` (`1-Projects/`) :**
   Appliquer [`Template-Projet.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Projet.md) avec :
   ```yaml
   ---
   id: "AAAAMMJJHHMM"
   category: "Projet"
   status: "active"
   date_created: "AAAA-MM-JJ"
   tags:
     - projet
     - statut/actif
   areas:
     - "[[Domaine-Selectionne]]"
   themes:
     - "[[T-Theme-Selectionne]]"
   last_session: "AAAA-MM-JJ"
   sessions_count: 0
   total_real_duration: "0h00"
   total_estimated_manual: "0h00"
   total_time_saved: "0h00"
   ---
   ```
3. **Mise à Jour Automatique :**
   Tracer l'initialisation du projet dans `PATH_SYSTEM/log.md`.

---

### 3. Branche B : Création d'un Thème (`T-[Nom-Theme].md`) :
1. **Sollicitation des Métadonnées :**
   - Titre du thème (ex: `T-Nom-Theme`).
   - Domaine(s) de vie parent(s) rattaché(s) (`areas: ["[[Nom-Domaine]]"]`).
2. **Génération du Fichier dans `PATH_THEMES` (`2-Ressources/Themes/`) :**
   Appliquer [`Template-Theme.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Theme.md) avec :
   ```yaml
   ---
   id: "AAAAMMJJHHMM"
   category: "Theme"
   status: "active"
   date_created: "AAAA-MM-JJ"
   tags:
     - theme
   areas:
     - "[[Domaine-Selectionne]]"
   last_review: "AAAA-MM-JJ"
   ---
   ```
3. **Mise à Jour Automatique :**
   Tracer la création du thème dans `PATH_SYSTEM/log.md`.

---

### 4. Branche C : Création d'un Domaine de Vie (`[Nom-Domaine].md`) :
1. **Sollicitation des Métadonnées :**
   - Nom du domaine (ex: `Creativite`, `Sante`, etc.).
   - Standard d'exigence / Périmètre visé.
2. **Génération du Fichier dans `PATH_AREAS` (`3-Domaines-de-vie/`) :**
   Appliquer [`Template-Area.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Area.md).
3. **Mise à Jour Automatique :**
   - Inscrire la nouvelle entrée dans `PATH_AREAS/README.md`.
   - Tracer la création dans `PATH_SYSTEM/log.md`.

---

## Garde-fous & Sécurité
- Ne jamais écraser un fichier existant sans confirmation explicite.
- Toujours vérifier le préfixe (`P-` pour les projets, `T-` pour les thèmes).
- Rapport de sortie synthétique dans le chat sans bavardage.
