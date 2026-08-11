---
name: arca-create-note
description: Instancier et mailler de manière interactive et assistée une note Projet (P-), Thème (T-) ou Domaine de vie (Area) avec validation humaine, détection des thèmes inexistants et scan de justification.
---

# 🛠️ Skill : arca-create-note (Création, Chaînage & Validation Interactive)

## Déclencheurs & Alias Spécifiques

Ce skill est déclenché par l'une des commandes ou alias suivants :

| Commande Directe / Alias | Action Immédiate Exécutée |
| :--- | :--- |
| `create-project`, `create-projet`, `arca-create-project`, `brain-create-project` | 🚀 Instancie un **Projet (`P-`)** dans `PATH_PROJECTS` |
| `create-theme`, `arca-create-theme`, `brain-create-theme` | 📜 Instancie un **Thème (`T-`)** dans `PATH_THEMES` |
| `create-domaine`, `create-area`, `arca-create-area`, `brain-create-area` | 🧠 Instancie un **Domaine de Vie** dans `PATH_AREAS` |
| `create-note`, `arca-create-note`, `brain-create-note` | ❓ **Mode Interactif** (Demande quel type de note créer) |

---

## 🏛️ Règle d'Or : Validation Interactive Humaine
Avant toute modification ou création de fichier sur le disque, l'IA doit impérativement présenter ses propositions d'analyse (Domaines de vie rattachés, Thèmes MOCs existants, nouveaux Thèmes à créer, et Projets/Notes raccordés) et **demander la confirmation explicite de l'utilisateur** dans le chat.

---

## Workflow d'Exécution Séquentiel

### 1. Routage selon l'Alias Invoqué :
- **Si l'alias est spécifique** (ex: `create-project` ou `create-theme`) ➔ Sauter l'étape de qualification et exécuter directement la branche ciblée.
- **Si la commande est générique** (`create-note`) ➔ Demander à l'utilisateur : *"Quel type de note souhaites-tu créer : 1. Projet (`P-`), 2. Thème (`T-`), ou 3. Domaine de Vie ?"*

---

### 2. Branche A : Création d'un Projet (`P-[Nom-Projet].md`)

1. **Analyse Contextuelle & Scan des Connexions :**
   - Analyse le titre, le contexte ou la note brute source du projet.
   - Scanne le Vault (`PATH_AREAS` et `PATH_THEMES`) pour identifier :
     - Le ou les **Domaines de Vie** rattachés (`areas`).
     - Le ou les **Thèmes (MOCs) existants** rattachés (`themes`).
     - Les **Nouveaux Thèmes suggérés** qui n'existent pas encore dans `PATH_THEMES`.

2. **Proposition Interactive à l'Humain :**
   Présenter clairement le diagnostic dans le chat :
   - 📌 **Nom du projet proposé :** `P-[Nom-Projet]`
   - 🧠 **Domaine(s) de Vie rattaché(s) suggéré(s) :** `[[Domaine-1]]`, `[[Domaine-2]]`
   - 📜 **Thème(s) MOC existant(s) rattaché(s) :** `[[T-Theme-Existant]]`
   - 🆕 **Nouveau(x) Thème(s) suggéré(s) à créer :** `[[T-Nouveau-Theme]]` *(Non détecté dans `PATH_THEMES`)*
   - ❓ **Demande de validation :** *"Valides-tu ce maillage ? Souhaites-tu instancier dans la foulée le(s) nouveau(x) thème(s) `[[T-Nouveau-Theme]]` ?"*

3. **Exécution & Chaînage (Après validation explicite) :**
   - Instancier `P-[Nom-Projet].md` dans `PATH_PROJECTS` avec [`Template-Projet.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Projet.md).
   - Si validé par l'utilisateur, **enchaîner immédiatement la création** du nouveau thème `T-Nouveau-Theme.md` dans `PATH_THEMES` avec [`Template-Theme.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Theme.md).
   - **Raccordement bidirectionnel :** Renseigner la note de projet dans la section `### 🏁 Projets & chantiers de l'année` des fiches de Domaines de Vie rattachées (`PATH_AREAS`).
   - Journaliser l'instanciation et le maillage dans `PATH_SYSTEM/log.md`.

---

### 3. Branche B : Création d'un Thème (`T-[Nom-Theme].md`)

1. **Analyse Contextuelle & Scan des Connexions :**
   - Analyse le périmètre et la vision du thème.
   - Scanne `PATH_AREAS` pour identifier le ou les **Domaines de Vie parents** (`areas`).
   - Scanne `PATH_PROJECTS`, `PATH_ARCHIVES` et `PATH_NOTES` pour repérer les **Projets et Notes existants** rattachables à ce thème.

2. **Proposition Interactive à l'Humain :**
   Présenter clairement le diagnostic dans le chat :
   - 📜 **Nom du Thème proposé :** `T-[Nom-Theme]`
   - 🧠 **Domaine(s) de Vie parent(s) suggéré(s) :** `[[Domaine-Parent]]`
   - 🔗 **Projets & Notes existants à lier :** `[[P-Projet-1]]`, `[[Note-1]]`
   - ❓ **Demande de validation :** *"Confirmes-tu l'ouverture de ce thème et le raccordement de ces projets et notes existants ?"*

3. **Exécution (Après validation explicite) :**
   - Instancier `T-[Nom-Theme].md` dans `PATH_THEMES` avec [`Template-Theme.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Theme.md).
   - Mettre à jour les métadonnées `themes` des projets et notes validés.
   - Raccorder le thème aux fiches de Domaines parents.
   - Journaliser l'action dans `PATH_SYSTEM/log.md`.

---

### 4. Branche C : Création d'un Domaine de Vie (`[Nom-Domaine].md`)

1. **Scan de Justification & Audit du Vault :**
   - Scanne l'ensemble du Vault (`PATH_PROJECTS`, `PATH_ARCHIVES`, `PATH_THEMES`, `PATH_NOTES`) pour faire un **bilan de justification** : repérer les projets actifs, projets archivés, thèmes et notes orphelins qui légitiment l'ouverture de ce nouveau Domaine de responsabilité.

2. **Proposition Interactive & Rapport de Justification :**
   Présenter à l'utilisateur :
   - 🧠 **Nom du Domaine de Vie proposé :** `[Nom-Domaine]`
   - 📊 **Analyse de Justification (Contenu du Vault concerné) :**
     - Projets actifs & archivés à regrouper : `[[P-Projet-A]]`, `[[P-Projet-B]]`
     - Thèmes associés : `[[T-Theme-X]]`
   - 🎯 **Périmètre visé & Standard d'exigence proposé.**
   - ❓ **Demande de validation :** *"Confirmes-tu la création de ce Domaine de Vie et le rattachement de ces projets et thèmes ?"*

3. **Exécution (Après validation explicite) :**
   - Instancier `[Nom-Domaine].md` dans `PATH_AREAS` avec [`Template-Area.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Area.md).
   - Inscrire l'entrée dans `PATH_AREAS/README.md`.
   - Mettre à jour les métadonnées `areas` des projets et thèmes rattachés.
   - Journaliser l'action dans `PATH_SYSTEM/log.md`.

---

## 🛡️ Garde-fous & Sécurité
- **Bannissement du Tiret Cadratin :** Ne jamais utiliser de tiret cadratin (`—`) dans les synthèses ou notes rédigées pour l'utilisateur (remplacer par des deux-points `:`, des virgules `,` ou des parenthèses `()`).
- **Seuil de Modification Massive :** Si une création ou un maillage implique plus de 3 fichiers simultanés, solliciter une confirmation explicite dédiée dans le chat.
- **Transparence & Traçabilité :** Fournir un rapport d'exécution clair et concis dans le message de sortie.
