---
date_created: 2026-09-05
title: "👋 Bienvenue sur Arca-BrainOS : Guide de Démarrage Rapide (3 Minutes)"
tags:
  - onboarding
  - guide
  - arca-brainos
status: #actif
---

# 👋 Bienvenue dans votre Bac à Sable Arca-BrainOS !

Félicitations, vous venez d'ouvrir le **Starter Vault Arca-BrainOS**. 

Ce coffre est un environnement prêt à l'emploi, entièrement autonome et sécurisé. Vos données sont hébergées à **100 % en local dans des fichiers Markdown pur (`.md`)** : vous gardez le contrôle total de vos notes, sans aucun enfermement propriétaire.

> 💡 **Contexte d'expérimentation :** Ce système a été conçu pour un usage personnel sur votre machine personnelle. Prenez le temps de l'explorer librement !

---

## ⚡ Prise en Main Rapide en 2 Étapes

### 1️⃣ Étape 1 : Lancer Votre Assistant IA (1 Minute)

Arca-BrainOS est piloté par un **agent IA local** capable de lire, mailler et organiser vos notes selon les instructions de la Constitution système (`_Arca-BrainOS/AGENTS.md`).

Ouvrez un terminal dans le dossier de ce coffre et lancez votre co-pilote IA préféré :

- **Option A (Recommandée & Gratuite) : Google Antigravity CLI / Gemini CLI**  
  Rapide, quotas très généreux et gratuit avec une clé API Google AI Studio.
- **Option B (Avancée & Puissante) : Claude Code**  
  Pour les utilisateurs disposant d'un compte Anthropic / Claude.
- **Option C (Multi-Modèles & Local) : OpenCode**  
  Idéal pour connecter des modèles locaux (Ollama, Qwen, DeepSeek) ou des API souveraines.
- **Option D (Interface Graphique) : Cursor ou VS Code**  
  Ouvrez simplement le dossier du coffre dans l'éditeur et activez le panneau de chat IA.

---

### 2️⃣ Étape 2 : Votre Premier "Run Magique" en 30 Secondes

Pour constater immédiatement comment l'IA élimine la friction d'organisation sans altérer vos idées, une note brute de démonstration est déjà déposée dans votre dossier [`0-Inbox/`](0-Inbox/) :  
👉 [`0-Inbox/Idee-Brute-Architecture-Agentique.md`](0-Inbox/Idee-Brute-Architecture-Agentique.md)

#### 🪄 L'Action à mener :
Dans le chat de votre terminal IA, tapez simplement :
```bash
arca-inbox-process
```
*(ou dites en langage naturel : "Trie mon Inbox et qualifie les nouvelles notes")*

#### 👁️ Ce qui se passe sous vos yeux en 10 secondes :
1. L'agent analyse le contenu de la note brute sans en perdre un seul mot.
2. Il normalise le frontmatter YAML (`category: idea`, `tags`, `status`).
3. Il extrait l'idée clé, conserve fidèlement votre texte d'origine (*Raw Note*), et détecte un lien vers le projet de démonstration [`1-Projects/P-Projet-IA-Souveraine.md`](1-Projects/P-Projet-IA-Souveraine.md).
4. Il range automatiquement la note qualifiée dans [`2-Ressources/Notes/`](2-Ressources/Notes/) : votre Inbox est à nouveau propre (**Inbox Zero**) !

---

## 🎯 Deuxième Expérience : Cadrer une Session de Deep Work

Pour démarrer une séance de travail productive sur un projet sans vous demander par quoi commencer :

Tapez dans votre terminal IA :
```bash
arca-resume 1-Projects/P-Projet-IA-Souveraine.md
```

**Ce que fait votre co-pilote :**
- Il scanne l'état d'avancement du projet et les derniers jalons.
- Il vous propose une **Intention de Session** claire avec 2 ou 3 actions prioritaires.
- Il initialise le journal de bord horodaté au sommet de la note projet.

À la fin de votre session de travail, tapez `arca-close-session 1-Projects/P-Projet-IA-Souveraine.md` pour calculer le temps économisé et archiver vos accomplissements.

---

## 🚀 Troisième Expérience : Créer Votre Propre Projet en 1 Ligne

Vous avez un projet personnel ou professionnel à lancer (ex: rénovation, apprentissage, santé, voyage ou écrit) ?

Tapez simplement dans votre terminal IA :
```bash
create-project Mon Super Projet
```

**Ce que fait votre co-pilote IA :**
1. Il analyse l'intitulé et la nature de votre projet (action pratique sans thème vs projet intellectuel avec base de connaissances).
2. Il scanne vos **Domaines de Vie** dans `3-Domaines-de-vie/` :
   - S'il trouve un domaine existant adapté, il propose de l'y rattacher.
   - Si votre projet concerne un nouveau pan de votre vie (ex: `Logement`, `Sante`, `Finance`), il vous propose **d'instancier automatiquement ce nouveau Domaine de Vie** et de l'enregistrer dans l'index.
3. Si le projet nécessite un Thème MOC de connaissances, il propose également de le rattacher ou de le créer.
4. Dès votre validation dans le chat, votre note projet `P-[Nom].md` est prête avec ses jalons pour votre premier `arca-resume` !

---

## 📊 Quatrième Expérience : Découvrir Votre Cockpit Visuel (`Home.md`)

Une fois vos premières notes et projets en place, Arca-BrainOS propose un tableau de bord exécutif central : [`Home.md`](Home.md). Il regroupe la vue d'ensemble de vos projets actifs, votre focus hebdomadaire et vos dernières fiches de connaissances.

Pour animer les jauges dynamiques du cockpit via le plugin communautaire standard **Dataview** (optionnel mais fortement recommandé) :

1. Dans Obsidian, ouvrez les **Paramètres** (icône d'engrenage en bas à gauche) $\rightarrow$ **Plugins communautaires**.
2. Cliquez sur **Parcourir**, cherchez **Dataview**, puis cliquez sur **Installer** et **Activer**.
3. Dans la liste des plugins installés, ouvrez les options de **Dataview** et vérifiez que ces deux options sont cochées :
   - ✅ **Enable JavaScript Queries** (`dataviewjs`)
   - ✅ **Enable Inline JavaScript Queries**
4. Ouvrez [`Home.md`](Home.md) : votre cockpit exécutif s'anime automatiquement avec vos vrais projets et vos notes !

---

## 🗺️ Explorer la Structure du Coffre (Méthode PARA)

Le coffre est organisé selon la méthode **PARA** adaptée à l'assistance par IA :

- **`0-Inbox/`** : Point d'entrée unique de toutes vos captures, idées volantes et liens d'articles.
- **`1-Projects/`** : Vos projets actifs en cours, jalonnés avec des objectifs précis (`P-[Nom].md`).
- **`2-Ressources/`** : Votre base de connaissances pérenne, découpée en 3 zones étanches :
  - `Notes/` : Vos réflexions et écrits humains.
  - `Themes/` : Vos fiches thématiques d'indexation MOC (`T-[Sujet].md`).
  - `IA-generated/` : Le conteneur isolé où l'IA range ses synthèses conceptuelles (`AI-Distil-...`).
- **`3-Domaines-de-vie/`** : Vos domaines de responsabilité permanents (Santé, Travail, Créativité...).
- **`4-Archives/`** : Le stockage à froid de vos projets finalisés.
- **`_Arca-BrainOS/`** : Le moteur agentique portable (compétences `skills/`, fiches de processus `process/` et modèles `templates/`).

---

## 💬 Une Question ? Échanger & Contribuer

Ce système est une aventure collaborative et ouverte. Si vous rencontrez la moindre difficulté lors de l'installation, si vous avez une idée d'amélioration ou si vous souhaitez partager vos premiers cas d'usage :

- Ouvrez une discussion ou une issue sur le dépôt GitHub : **[github.com/Arca-Brain/Arca-BrainOS/issues](https://github.com/Arca-Brain/Arca-BrainOS/issues)**
- Pour explorer la vision philosophique complète, lisez le **[Manifeste Arca-BrainOS](../../MANIFESTO.fr.md)**.
- Le dépôt officiel du projet : **[github.com/Arca-Brain/Arca-BrainOS](https://github.com/Arca-Brain/Arca-BrainOS)**
