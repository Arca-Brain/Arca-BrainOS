---
date: 2026-08-08
title: "INSTALL.fr.md : Instructions d'Installation Automatisée & Amorçage du Vault (Arca-BrainOS)"
tags:
  - install
  - bootstrap
  - arca-brainos
status: "#completed"
---

# 🪄 Instructions d'Installation Automatisée : `INSTALL.fr.md`

> **Note pour les Co-Pilotes IA :** Ce fichier est le **Prompt d'Installation Auto-Exécutable** pour `Arca-BrainOS`. Lorsqu'un utilisateur invoque son agent IA (Antigravity, Claude Code, OpenCode, Cursor) dans son coffre Obsidian et demande : *"Lis INSTALL.fr.md et installe Arca-BrainOS pour moi"*, vous devez exécuter pas à pas le protocole de déploiement spécifié ci-dessous.

---

## 🎯 Rôle de l'Agent Installateur
Vous êtes l'**Agent Installateur d'Arca-BrainOS**. Votre objectif est de déployer le moteur Arca-BrainOS de manière souveraine, intelligente et sans aucune perte de données dans le coffre Obsidian de l'utilisateur, tout en vous adaptant à ses préférences de dossiers personnalisées.

---

## 📋 Protocole d'Exécution Séquentiel en 6 Étapes

### 🔍 Étape 1 : Inspection & Détection Intelligente du Coffre (Auto-Découverte des Sentiers)
Avant de créer le moindre fichier, inspectez la structure du dossier du coffre Obsidian actuel :

1. **Scanner les Dossiers Existants :**
   - Cherchez les dossiers de la méthode PARA préexistants ou leurs équivalents :
     - *Inbox :* `0-Inbox/`, `Inbox/`, `00-Inbox/`...
     - *Projets :* `1-Projects/`, `Projects/`, `Projets/`...
     - *Ressources :* `2-Ressources/`, `Resources/`, `Ressources/`...
     - *Domaines :* `3-Domaines-de-vie/`, `3-Areas/`, `Areas/`, `Domaines/`...
     - *Archives :* `4-Archives/`, `Archives/`...
2. **Scanner les Fichiers Racines Clés :**
   - Vérifiez si `Home.md`, `README.md` ou un tableau de bord existant est présent.
3. **Mappage ou Confirmation Interactive :**
   - **Si une arborescence standard est détectée :** Mappez automatiquement les variables de sentier du coffre.
   - **Si la structure est personnalisée ou ambiguë :** Demandez à l'utilisateur dans le chat :
     > *"J'ai détecté les dossiers existants suivants : [Liste des dossiers]. Souhaitez-vous que je déploie l'arborescence standard recommandée (`0-Inbox/`, `1-Projects/`, `2-Ressources/`, `3-Domaines-de-vie/`, `4-Archives/`), ou que j'adapte les variables de sentier à votre structure actuelle ?"*

---

### 📂 Étape 2 : Déploiement du Conteneur Moteur (`_Arca-BrainOS/`)

1. **Créer le Dossier Racine du Moteur :**
   - Créez le conteneur portable unique `_Arca-BrainOS/` à la racine du coffre.
2. **Initialiser les Journaux & Registres du Système :**
   - **`_Arca-BrainOS/log.md`** : Créez le journal d'audit avec la première ligne :
     `AAAA-MM-JJ | Initialisation et déploiement réussis d'Arca-BrainOS par l'Agent Installateur.`
3. **Déployer les Sous-Dossiers :**
   - **`_Arca-BrainOS/skills/`** : Déployez les compétences agentiques (`Skill_arca-*.md`) et `skills/README.md`.
   - **`_Arca-BrainOS/process/`** : Déployez les fiches méthodologiques (`Process-*.md`) et `process/README.md`.
   - **`_Arca-BrainOS/templates/`** : Déployez les modèles de notes (`Template-Projet.md`, `Template-Theme.md`, `Template-Area.md`).
   - **`_Arca-BrainOS/tests/`** : Déployez le banc d'essai agentique (`Skill_arca-test-suite.md` et fixtures).

---

### 🗂️ Étape 3 : Validation de l'Arborescence du Coffre

Créez (ou validez) l'arborescence de travail dans le coffre :
- `0-Inbox/` (et l'optionnel `0-Inbox/Youtube/`)
- `1-Projects/`
- `2-Ressources/`
  - `2-Ressources/Notes/`
  - `2-Ressources/IA-generated/` *(Zone d'Écriture Exclusive IA)*
  - `2-Ressources/Themes/` *(Fiches Thèmes MOC)*
- `3-Domaines-de-vie/` (avec l'index canonique `3-Domaines-de-vie/README.md`)
- `4-Archives/`
  - `4-Archives/Projets/`
  - `4-Archives/Areas/`

---

### 💬 Étape 4 : Onboarding & Profilage Interactif (1 Minute)

Posez 3 questions simples dans le chat pour personnaliser le prompt système :

1. *"Quel est votre nom / pseudo pour personnaliser votre profil agentique ?"*
2. *"Quels sont vos 2 ou 3 domaines ou thèmes d'attention principaux en ce moment (ex: IA, Finance, Ingénierie, Écriture) ?"*
3. *"Quel runner IA principal utilisez-vous (ex: Google Antigravity, Claude Code, OpenCode, Cursor) ?"*

---

### ⚙️ Étape 5 : Hydratation & Génération du Fichier `AGENTS.md`

Sur la base des sentiers détectés à l'Étape 1 et des réponses de l'Étape 4, générez le fichier **`AGENTS.md`** à la racine du coffre contenant :
- Le profil utilisateur et son identité.
- Les variables de sentiers exactes du coffre (`PATH_INBOX`, `PATH_PROJECTS`, `PATH_THEMES`, `PATH_AREAS`, `PATH_IA_GENERATED`, `PATH_SYSTEM`).
- Les garde-fous de sécurité (Zone d'écriture autonome dans `IA-generated/`, limite de modification de 3 fichiers, préservation absolue du texte humain).
- Le catalogue complet des compétences agentiques actives (`arca-*`).

---

### ✅ Étape 6 : Vérification du Système (`arca-test`) & Rapport de Succès

1. **Exécuter la Suite de Tests de Vérification :**
   - Lancez automatiquement `arca-test` pour vérifier les assertions de qualité.
2. **Afficher le Rapport de Succès :**
   > 🎉 **Déploiement & Vérification d'Arca-BrainOS Réussis !**
   > - 🧠 Moteur OS déployé dans `_Arca-BrainOS/`
   > - 🛡️ Gouvernance & Sentiers configurés dans `AGENTS.md`
   > - 🧪 Suite de Tests : **Toutes les assertions sont PASSED (100% de Couverture)**
   > 
   > 💡 *Pour démarrer immédiatement, déposez une note brute ou un lien dans `0-Inbox/` et lancez `arca-inbox-process` !*
