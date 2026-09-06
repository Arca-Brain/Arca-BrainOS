---
name: arca-archive-project
description: Clôturer proprement et archiver physiquement une note projet vers 4-Archives/Projets/, avec audit des tâches résiduelles, proposition optionnelle de capitalisation (note réflexive ou règle dans memory.md), mise à jour du Domaine de vie et traçabilité.
---

# 🛠️ Skill : arca-archive-project (Clôture Finale & Archivage de Projet)

- **Processus de Référence :** [[Process-Archivage-de-Projet]]

## Déclencheurs & Alias Spécifiques
Ce skill est déclenché par l'une des commandes suivantes, suivie du nom ou lien du projet :
- `arca-archive-project [[P-Nom-Projet]]`
- `archive-project [[P-Nom-Projet]]`
- `brain-archive-project [[P-Nom-Projet]]`

---

## 🏛️ Règle d'Or : Validation Interactive & Frugalité
1. **Validation préalable :** L'agent ne déplace jamais un projet sans avoir reçu la confirmation explicite de l'utilisateur dans le chat.
2. **Capitalisation non intrusive :** L'extraction d'apprentissages est toujours proactive mais optionnelle. Si l'utilisateur souhaite archiver directement, l'agent s'exécute immédiatement sans insister.
3. **Sanctuarisation d'AGENTS.md :** Les règles ou habitudes apprises sont orientées vers `_Arca-BrainOS/memory.md`, jamais dans `AGENTS.md`.
4. **Nommage Naturel :** Toute note de concept ou retour d'expérience créé est nommé naturellement dans `2-Ressources/Notes/[Titre].md` avec le tag `apprentissage`.

---

## Workflow d'Exécution Séquentiel

### 1. Chargement & Audit des Tâches Résiduelles
- Charge la note du projet cible (`P-[Nom-Projet].md`) située dans `PATH_PROJECTS` (ou `PATH_INCUBATION`).
- Scanne les listes de tâches pour identifier d'éventuelles actions non cochées (`- [ ]`) :
  - Si des tâches restent ouvertes, l'agent les liste et demande l'arbitrage :
    - Les cocher si terminées (`[x]`).
    - Les rayer si abandonnées (`~[ ]~`).
    - Les transférer sous forme de graines d'idées brutes dans la section `## 🌱 Idées Futurs (Backlog)` du Domaine parent.
- Demande de validation : *"Toutes les tâches sont traitées. Confirmes-tu l'archivage définitif de `P-[Nom-Projet]` ?"*

---

### 2. Détection d'Apprentissage & Capitalisation (Optionnelle)
- L'agent parcourt rapidement le `## 🪵 Journal de Bord des Sessions` du projet pour repérer :
  - Un enseignement conceptuel, méthodologique ou un REX réutilisable.
  - Une règle de travail ou préférence d'interaction IA formulée en session.
- Présente une proposition synthétique à l'utilisateur :
  - **Option Note de Savoir :** Création d'une note réflexive standard dans `PATH_NOTES` (`2-Ressources/Notes/[Titre-Clair].md`, tag `apprentissage`, reliée à son Thème MOC).
  - **Option Règle Système :** Ancrage d'une micro-directive dans `_Arca-BrainOS/memory.md` (soumise aux critères anti-pollution).
  - **Option Archivage Direct :** Passage immédiat à l'archivage physique sans création de note.

---

### 3. Scellement du Frontmatter YAML
- Met à jour le frontmatter de la note projet :
  - `status: "completed"`
  - Remplace le tag `statut/actif` (ou `statut/someday`) par `statut/termine`.
  - Fige la date `last_session: "AAAA-MM-JJ"` avec la date du jour.

---

### 4. Déplacement Physique vers les Archives
- Exécute le déplacement atomique du fichier vers le dossier d'archives :
  `mv 1-Projects/P-[Nom-Projet].md 4-Archives/Projets/` (ou depuis `1-Projects/_Incubation/`).

---

### 5. Raccordement & Actualisation du Domaine de Vie
- Scanne les Domaines parents déclarés dans le champ `areas` du projet (`3-Domaines-de-vie/`).
- Dans la section `### 🏁 Projets & chantiers de l'année` du Domaine parent, ajoute la mention de clôture :
  `- [[P-Nom-Projet]] : [Description rapide] (✔ Terminé)`
- La table Dataview `### 📦 Projets Archivés & Terminés` du Domaine prend immédiatement en charge le projet.
- Le tableau de bord `Home.md` met à jour ses compteurs en temps réel (décrément Projets Actifs, incrément Archives, cumul du temps IA préservé).

---

### 6. Traçabilité Système
- Ajoute une ligne d'action unique dans `_Arca-BrainOS/log.md` :
  `[AAAA-MM-JJ HH:mm] - Action IA (Archivage) : Projet [[P-Nom-Projet]] archivé vers 4-Archives/Projets/ (statut: completed)`
