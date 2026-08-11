---
date: 2026-08-08
title: "Arca-BrainOS : Version Officielle Open-Source GitHub"
description: "README officiel en Français pour la publication open-source d'Arca-BrainOS sur GitHub."
tags:
  - readme
  - github
  - open-source
  - arca-brainos
status: "#completed"
---

# 🧠 Arca-BrainOS

> *"Mon arche n'est pas un refuge, c'est un moteur... Le rêve conçoit, mais seule l'action accomplit."*  
> **Fernando Pessoa**  
>  
> *(Inspiré de la célèbre malle en bois de Fernando Pessoa, "A Arca", contenant des milliers de fragments, manuscrits et hétéronymes en attente de devenir un univers. Arca-BrainOS est ce moteur d'exécution pour votre esprit numérique.)*

---

**Workflow agentique souverain & co-pilote local pour Obsidian**

🇬🇧 **[Read the English version (README.md)](README.md)**

[![Obsidian](https://img.shields.io/badge/Obsidian-Vault%20Ready-7C3AED?style=flat-square&logo=obsidian&logoColor=white)](https://obsidian.md)
[![Licence: Hybride AGPLv3 / CC BY-NC-SA 4.0](https://img.shields.io/badge/Licence-Hybride%20AGPLv3%20%2F%20CC%20BY--NC--SA%204.0-blue?style=flat-square)](LICENSE)
[![LLM Agnostique](https://img.shields.io/badge/LLM-Agnostique%20%26%20Portable-emerald?style=flat-square)](#-principes-cl%C3%A9s-de-conception)
[![Vitesse ROI](https://img.shields.io/badge/ROI-Vitesse%20x3%20⚡-orange?style=flat-square)](#-roi-terrain-mesur%C3%A9--m%C3%A9triques)
[![Développé avec Google Antigravity](https://img.shields.io/badge/D%C3%A9velopp%C3%A9_avec-Google%20Antigravity-4285F4?style=flat-square&logo=google&logoColor=white)](https://github.com/Arca-Brain/Arca-BrainOS)

**[Quickstart](#-quickstart-onboarding-en-1-minute)** · **[Guide Onboarding](GETTING_STARTED.fr.md)** · **[Manifeste](MANIFESTO.fr.md)** · **[Compétences Agentiques](#-larsenal-des-comp%C3%A9tences-agentiques)** · **[Architecture](#-architecture--topographie-du-vault-conception-d%C3%A9coupl%C3%A9e)** · **[Contribuer](CONTRIBUTING.fr.md)** · **[FAQ](#-faq--gestion-des-risques)**


---

> 🎯 **Concept Clé :** Passez des pensées éparpillées et des outils IA fragmentés à un système d'exploitation souverain et AI-native qui exécute vos flux cognitifs directement au cœur de votre coffre Obsidian local.


### ⭐ Si Arca-BrainOS vous est utile, ajoutez une étoile au dépôt GitHub !

Les étoiles aident d'autres penseurs et bâtisseurs à découvrir le projet et à le faire progresser.

[![Star Arca-BrainOS sur GitHub](https://img.shields.io/badge/Star%20Arca--BrainOS%20sur%20GitHub-⭐-8B5CF6?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Arca-Brain/Arca-BrainOS)


---

## 💥 Le Problème : Pourquoi la plupart des Second Brains s'éteignent

Construire un Second Cerveau (PKM) se transforme souvent en un piège de friction et de maintenance :

* **Écosystèmes fragmentés & SaaS propriétaires :** Vos pensées, documents et flux de travail sont dispersés entre de multiples dépôts, onglets web et plateformes SaaS qui deviennent de plus en plus les gardiens propriétaires de vos données personnelles, verrouillant votre contexte dans des silos cloud.
* **Lourde charge de maintenance administrative :** Fatigue mentale constante liée au ménage manuel du coffre : trier l'inbox, déplacer des fichiers, mettre en forme des notes et maintenir les liens.
* **Le piège de la configuration :** Passer des dizaines d'heures à essayer de configurer un système efficace parfait dans son coffre (bidouiller des scripts Dataview, des snippets CSS et des arborescences complexes) au lieu d'exécuter des projets réels et d'obtenir des résultats concrets.

---

## 🛡️ La Solution : Arca-BrainOS

**Arca-BrainOS** est un système d'exploitation open-source et AI-native conçu pour **Obsidian**. Il équipe votre coffre d'une flotte de **compétences agentiques autonomes (`Skill_arca-*.md`)** qui exécutent les tâches cognitives récurrentes, structurent vos connaissances et co-pilotent vos sessions de Deep Work.

> 📜 **Philosophie & Vision :** Vous souhaitez comprendre la mutation anthropologique, le *Pharmakon* de Stiegler et la symbiose organologique derrière cette architecture ? Lisez **[Le Manifeste du Workflow Augmenté (MANIFESTO.fr.md)](MANIFESTO.fr.md)**.

```text
       [ Flux entrants : Vidéos, Livres, Web, Transcripts ]
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │  1. Capture & Tri (0-Inbox/ & Youtube)       │
        └──────────────────────────────────────────────┘
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │ 2. Distillation & Ancrage Thématique (T-)    │
        └──────────────────────────────────────────────┘
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │ 3. Exploration & Santé du Vault (RAG/Audit)  │
        └──────────────────────────────────────────────┘
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │ 4. Deep Work & Exécution (Projets & ROI)     │
        └──────────────────────────────────────────────┘
                                │
                                ▼
           [ Résultats à haut impact & Vitesse x3 ]
```

---

## ⚡ ROI Terrain Mesuré & Métriques

Arca-BrainOS est fondé sur des **données empiriques réelles**, suivies en continu sur des projets réels d'ingénierie, de recherche et d'écriture.

> 💡 **Contexte Crucial :** Ces métriques n'ont pas été mesurées sur un coffre démo vide. Elles ont été obtenues sur un **coffre réel préexistant** contenant des centaines de notes héritées. Une fois convaincus de la puissance du système, les co-pilotes IA exécutent un rétrofit progressif et propre des notes historiques, du YAML et des fiches Thèmes.

| Métrique                         |       Valeur Mesurée        | Signification Terrain                              |
| :------------------------------- | :-------------------------: | :------------------------------------------------- |
| **Ligne de Base du Coffre**      |  **Coffre Réel Préexistant** | Testé sur de vraies notes historiques, pas un démo |
| **Sessions de Deep Work Clôturées**|       **62 sessions**       | Ingénierie réelle & production intellectuelle      |
| **Temps Réel Investi avec IA**   |          **80h40**          | Temps de session suivi avec Arca-BrainOS           |
| **Temps Estimé Sans IA**         |         **~258h00**         | Référentiel de travail de la connaissance (MIT/Harvard) |
| **Temps Net Économisé**          |       **🚀 +177h20**        | Effort cognitif direct libéré                      |
| **Multiplicateur de Vitesse**    |          **⚡ x3**          | **Exécution de projet 3x plus rapide**             |

---

## 🧩 Les 3 Phases d'Adoption de l'IA

La plupart des travailleurs de la connaissance restent bloqués en Phase 1 ou 2 :

1. **Phase 1 : Usage Opportuniste (Prompting ad-hoc) :** Poser des questions isolées dans des interfaces web ChatGPT/Claude. Forte friction, mémoire nulle.
2. **Phase 2 : Usage Fragmenté (Gems & Projects) :** Créer des silos dans des plateformes propriétaires (ChatGPT Projects, Claude Projects). Le contexte est enfermé dans des clouds tiers.
3. **Phase 3 : Intégration Systémique (Arca-BrainOS) :** Vos agents IA opèrent directement sur votre coffre Markdown local avec un contexte complet en temps réel. **Zéro enfermement, mémoire infinie.**

---

## 💎 Principes Clés de Conception

1. **Agnostique aux LLMs :** Fonctionne de manière fluide avec Claude 3.5 Sonnet, Gemini 1.5 Pro, GPT-4o ou des LLMs locaux (Ollama/oMLX).
2. **Standard Ouvert Markdown :** Fichiers `.md` 100% lisibles par l'humain. Aucune base de données propriétaire ni dépendance fermée.
3. **Préservation du Style Humain :** Les agents IA ne suppriment ni ne réécrivent jamais le texte rédigé par l'humain ; ils enrichissent les métadonnées et suggèrent des liens wikilinks.
4. **Extension Auto-Documentée :** Pour créer un nouveau skill ou process, **demandez simplement à votre agent LLM de le concevoir**. Votre co-pilote rédigera la logique et effectuera automatiquement toutes les mises à jour d'indexation (`AGENTS.md`, `skills/README.md`, `process/README.md`) tout en maintenant la conformité aux tests (`arca-test`).

---

## 🔌 L'Arsenal des Compétences Agentiques

Toutes les capacités agentiques sont des compétences modulaires en Markdown stockées dans `_Arca-BrainOS/skills/` et exécutables via vos terminaux IA (**Antigravity**, **Claude Code**, **OpenCode**, **Cursor**) :

### 📥 1. Capture & Tri
* `arca-inbox-process` : Normalise le YAML, nettoie les notes brutes et aiguille les flux entrants.
* `arca-organize-idea` : Structuration d'idées brutes en notes d'action sans dénaturer le texte humain d'origine.
* `arca-youtube` : Extrait la transcription et les métadonnées de vidéos YouTube pour créer une note brute.

### 🧪 2. Distillation & Ancrage Thématique (*The Killer Feature*)
* `arca-distill` : Master skill d'ingestion média (Synthèse $\rightarrow$ Ancrage $\rightarrow$ Archivage $\rightarrow$ Analyse d'impact).
* `arca-synthesize` : Rédige des synthèses conceptuelles structurées (`AI-Distil-...`) dans `/2-Ressources/IA-generated/`.
* `arca-converge` : Ancre les distillations dans les fiches Thèmes (`T-`) via des liens wikilinks.
* `arca-impact` : Scanne les projets actifs (`P-`) pour proposer des tâches concrètes découlant des nouvelles connaissances.

### 🔍 3. Exploration & Maintenance du Vault
* `arca-query` : Co-pilote RAG conversationnel créant des ponts cognitifs entre des idées distantes.
* `arca-audit` : Diagnostic de santé PARA, détection des notes orphelines, liens brisés et suivi ROI.
* `arca-test-suite` : Banc d'essai agentique automatisé exécutant les assertions de non-régression.

### 🪵 4. Deep Work & Exécution
* `arca-resume` : Cadrage cognitif des sessions de travail (synthèse de l'avancement et définition de l'intention).
* `arca-close-session` : Clôture des sessions de Deep Work, tenue du journal de bord du projet et calcul du ROI.
* `arca-create-note` : Instanciation rapide via raccourcis direct (`create-project`, `create-theme`, `create-domaine`).

---

## 📂 Architecture & Topographie du Vault (Conception Découplée)

Arca-BrainOS s'appuie sur une **architecture strictly découplée en 2 parties** :

1. **Partie A : Le Moteur OS (`_Arca-BrainOS/`) :** Un conteneur unique et 100% portable regroupant les skills, process, templates, tests et `AGENTS.md`.
2. **Partie B : Votre Contenu 2nd Brain (Coffre existant ou nouveau) :** Vos notes personnelles, projets et dossiers. **Arca-BrainOS est 100% agnostique de votre arborescence** : adaptez simplement les variables de sentiers dans `AGENTS.md` (`PATH_INBOX`, `PATH_PROJECTS`, `PATH_THEMES`, `PATH_AREAS`) pour raccorder le moteur à votre propre structure !

```text
Votre-Coffre-Obsidian/
├── _Arca-BrainOS/                # 🧠 PARTIE A : Le Conteneur Moteur OS (100% Portable)
│   ├── AGENTS.md                 # Prompt Système Maître & Variables de Sentier (PATH_PROJECTS, etc.)
│   ├── log.md                    # Journal d'audit chronologique (1 ligne / action)
│   ├── skills/                   # 🔌 Compétences Agentiques Modulaires (Skill_arca-*.md)
│   ├── process/                  # 📚 Fiches Méthodologiques Embarquées (Process-*.md)
│   ├── templates/                # 📄 Modèles de Notes (Projet, Theme, Area)
│   └── tests/                    # 🧪 Banc d'Essai Agentique & Fixtures
│
├── Home.md                       # Cockpit Exécutif Optionnel (Inclus dans starter-vault)
├── 0-Inbox/                      # 🧠 PARTIE B : Vos Contenus 2nd Brain (Sentiers Configurables)
├── 1-Projects/                   # Projets Actifs (P-...)
├── 2-Ressources/                 # Base de Connaissances
│   ├── Notes/                    # Notes humaines & journal
│   ├── IA-generated/             # Zone d'écriture exclusive IA (AI-Distil-...)
│   └── Themes/                   # Fiches Thèmes MOC (T-...)
├── 3-Domaines-de-vie/            # Domaines de responsabilité (Index canonique README.md)
└── 4-Archives/                   # Projets Terminés & Domaines Inactifs
```

---

## ⚡ Quickstart (Onboarding en 1 Minute)

> 💡 **Guide Opérationnel Détaillé :** Vous cherchez un guide d'onboarding pas-à-pas complet ? Consultez **[GETTING_STARTED.fr.md](GETTING_STARTED.fr.md)**.

### 1. Prérequis
* **[Obsidian](https://obsidian.md)** (v1.5+)
* **Plugin Communautaire Requis :**
  * **[Dataview Plugin](https://github.com/blacksmithgu/obsidian-dataview) :** Alimente le cockpit `Home.md` et les widgets de focus.
    * *Réglages requis :* Activez **"Enable JavaScript Queries"** (`dataviewjs`) et **"Enable Inline JavaScript Queries"** sous `Dataview > Settings`.
* **Runner Terminal IA :**
  * Un exécuteur de terminal IA exécuté localement dans votre coffre (ex: **Google Antigravity**, **Claude Code**, **OpenCode**, ou **Cursor**).

### 2. Installation (2 Options)

#### 📁 Option A : Ajouter à un coffre Obsidian EXISTANT (Dossier `_Arca-BrainOS/`)
Copiez le dossier moteur `_Arca-BrainOS/` à la racine de votre coffre actuel. Ouvrez votre terminal IA (Antigravity / Claude Code / OpenCode) dans votre coffre et lancez l'instruction d'amorçage de [`INSTALL.fr.md`](INSTALL.fr.md) :

```text
Lis https://github.com/Arca-Brain/Arca-BrainOS/blob/main/INSTALL.fr.md (ou INSTALL.fr.md local) et installe Arca-BrainOS pour moi.
```

*Votre Agent Installateur analysera votre arborescence existante, détectera vos sentiers personnalisés, déploiera `_Arca-BrainOS/`, configurera `AGENTS.md` et exécutera `arca-test` sans détruire ni écraser vos notes actuelles.*

#### 📦 Option B : Démarrer de zéro avec un coffre prêt-à-l'emploi (Dossier `starter-vault/`)
Téléchargez/copiez le dossier `starter-vault/` pré-configuré et ouvrez-le directement comme un nouveau coffre dans Obsidian. Tout est inclus "Out of the box" (`AGENTS.md` à la racine, cockpit `Home.md`, et structure PARA propre).

> 💡 **Conseil Recommandé :** Renommez le dossier `starter-vault/` avec un nom personnalisé qui a du sens pour vous (ex: `ArcaBrain`, `2ndBrain`, `MesNotes`, `MonCoffre`, etc.) avant ou après l'avoir ouvert dans Obsidian !

### 3. Test de Vérification
Dans votre terminal IA, lancez :
```bash
arca-test
```
*Votre agent exécutera les assertions automatisées pour vérifier la santé du coffre et la résolution des sentiers.*

---

## ❓ FAQ & Gestion des Risques

### En quoi Arca-BrainOS diffère-t-il d'Obsidian pur ou des chats IA isolés ?
Obsidian pur offre des fichiers Markdown locaux mais exige une organisation manuelle constante. Les chats IA isolés (ChatGPT, Claude) n'ont aucun contexte réel de vos notes passées. Arca-BrainOS fait le pont : vos agents IA opèrent directement sur vos fichiers locaux avec tout votre contexte, automatisant la friction tout en gardant 100% de vos données locales et lisibles.

### Que se passe-t-il si un agent fait une erreur ou si je veux annuler des modifications ?
Arca-BrainOS est conçu pour **zéro perte de données, une transparence totale et une récupération immédiate** :
* **Rollback en Session :** Si un agent interprète mal une consigne durant une session, dites-lui simplement dans le chat : *"Annule la dernière modification sur le fichier X"*. L'agent relira son historique et restaurera le fichier.
* **Garde-fou des 3 Fichiers :** Il est interdit aux agents de modifier ou créer plus de 3 fichiers hors de `/2-Ressources/IA-generated/` au cours d'un même workflow sans validation explicite.
* **Journal d'Audit Unique :** Chaque action est consignée dans `_Arca-BrainOS/log.md` (1 ligne par action avec horodatage).
* **Contrôle de Version Git :** Nous recommandons d'initialiser Git sur votre coffre (`git init`). Les rollbacks peuvent être exécutés instantanément via Git ou votre système de sauvegarde Obsidian Sync.

### Les agents IA vont-ils réécrire ou modifier mes notes rédigées à la main ?
**Non.** Arca-BrainOS fonctionne sous les garde-fous stricts définis dans `AGENTS.md` :
* **Zone d'Écriture Exclusive IA :** L'écriture autonome est isolée dans `/2-Ressources/IA-generated/` (synthèses `AI-Distil-...`).
* **Zone Supervisée :** Pour les notes humaines (`1-Projects/`, `2-Ressources/Notes/`, `3-Domaines-de-vie/`), les agents ne réécrivent jamais le texte humain. Ils proposent uniquement des liens wikilinks `[[...]]` ou mettent à jour le journal de bord lors de `arca-close-session`.

---

## 📜 Licence & Protection Stratégique

Arca-BrainOS est publié sous un modèle de **Licence Hybride / Double Licence** (voir [`LICENSE.md`](LICENSE.md)) :

* **Code, Skills & Scripts (`_Arca-BrainOS/skills/`, `tests/`, `scripts/`) :** Licence **GNU Affero General Public License v3.0 (GNU AGPLv3)**. Libre pour l'usage personnel et communautaire Open-Source.
* **Playbooks, Méthodes & Manifestes (`playbooks/`, `process/`, `MANIFESTO.md`) :** Licence **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)**. Usage libre à titre individuel ; revente commerciale, consulting d'entreprise payant ou intégration dans des produits tiers interdits sans accord écrit préalable.

> 💡 **Pourquoi ce choix de licence ?**  
> Nous croyons à un accès 100% libre et souverain pour les particuliers, chercheurs et passionnés. Cependant, nous choisissons **explicitement de ne PAS utiliser une licence permissive MIT** afin d'empêcher des sociétés ou éditeurs tiers de s'accaparer ce travail open-source, de le fermer dans des logiciels propriétaires ou de revendre nos méthodes à des fins commerciales sans contribuer en retour.

---

## 🙏 Remerciements & Inspirations

Arca-BrainOS s'appuie sur les travaux de pionniers de la productivité, du PKM et de l'ingénierie agentique :

* **[David Allen](https://gettingthingsdone.com)** : Auteur de **Getting Things Done (GTD)**.
* **[Sönke Ahrens](https://takesmartnotes.com)** : Auteur de ***How to Take Smart Notes*** (méthode Zettelkasten).
* **[Tiago Forte](https://fortelabs.com)** : Pionnier de **Building a Second Brain (BASB)**, du framework C.O.D.E et de la méthode P.A.R.A.
* **[Ryder Carroll](https://bulletjournal.com)** : Créateur de la méthode **Bullet Journal**.
* **[Daniel Miessler](https://danielmiessler.com)** : Pour le framework **Personal AI Infrastructure (PAI)**, **LifeOS** et les principes d'architecture modulaire UNIX (`_Arca-BrainOS/`).
* **[Eliott Meunier](https://www.youtube.com/@eliottmeunier)** : Éducateur et pionnier du PKM francophone sur Obsidian.
* **[Jeff Su](https://www.youtube.com/@JeffSu)** : Pour ses tutoriels sur l'optimisation des flux de travail.
* **[Obsidian.md](https://obsidian.md)** : Pour la création de la toile Markdown locale souveraine.
* **[Blacksmithgu & Communauté Dataview](https://github.com/blacksmithgu/obsidian-dataview)** : Pour le plugin Dataview.
* **Équipes Google Antigravity & Claude Code** : Pour le développement des exécuteurs agentiques en terminal local.

---

<p align="center">
  <i>Développé avec ❤️ pour les penseurs, bâtisseurs et passionnés du savoir.</i>
</p>
