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

<p align="center">
  <img src="assets/arcabrain_banner.jpg" alt="Bandeau Panoramique Arca-BrainOS" width="100%">
</p>

> *"Mon arche n'est pas un refuge, c'est un moteur... Le rêve conçoit, mais seule l'action accomplit."*  
> **Fernando Pessoa**  
>  
> *(Inspiré de la célèbre malle en bois de Fernando Pessoa, "A Arca", contenant des milliers de fragments, manuscrits et hétéronymes en attente de devenir un univers. Arca-BrainOS est ce moteur d'exécution pour votre esprit numérique.)*

---

**Un assistant IA local et souverain pour vos projets, vos notes de vie**

🇬🇧 **[Read the English version (README.md)](README.md)**

[![Obsidian](https://img.shields.io/badge/Obsidian-Vault%20Ready-7C3AED?style=flat-square&logo=obsidian&logoColor=white)](https://obsidian.md)
[![Licence: MIT](https://img.shields.io/badge/Licence-MIT-green.svg?style=flat-square)](LICENSE)
[![LLM Agnostique](https://img.shields.io/badge/LLM-Agnostique%20%26%20Portable-emerald?style=flat-square)](#-principes-cl%C3%A9s-de-conception)
[![Vitesse ROI](https://img.shields.io/badge/ROI-Vitesse%20x4%20⚡-orange?style=flat-square)](#-roi-terrain-mesur%C3%A9--m%C3%A9triques)

**[Quickstart](#-quickstart-onboarding-en-1-minute)** · **[Guide Onboarding](GETTING_STARTED.fr.md)** · **[Manifeste](MANIFESTO.fr.md)** · **[Architecture](#-architecture--topographie-du-vault-conception-d%C3%A9coupl%C3%A9e)** · **[Contribuer](CONTRIBUTING.fr.md)**

---

> 🎯 **Concept Clé :** Gardez vos notes et votre mémoire personnelle chez vous, hors des plateformes propriétaires. Arca-BrainOS dote vos assistants IA (en ligne de commande avec Claude Code, Antigravity, OpenCode, ou via des environnements comme Claude Cowork et Gemini Spark) d'une mémoire persistante directement dans vos fichiers Markdown. Vous restez 100% propriétaire de vos données et totalement libre de changer de modèle IA à tout moment sans rien perdre de votre contexte.

---

## 💥 Le Problème : Le fossé entre pensée humaine et agents IA

1. **L'amnésie systématique des agents IA :** Qu'ils s'exécutent en terminal (Claude Code, Antigravity, OpenCode) ou en espace de travail de bureau (Claude Cowork, Gemini Spark), les agents IA sont surpuissants mais amnésiques. À chaque nouvelle session, tout le contexte métier s'évapore et l'interaction repart de zéro.
2. **Le piège de l'intendance documentaire :** Organiser ses données personnelles et ses notes tourne souvent au cauchemar : tri manuel incessant, maintenance fastidieuse des liens et perte de temps dans la configuration d'outils au lieu de faire avancer ses projets réels.
3. **L'enfermement dans les silos propriétaires :** Confier sa mémoire à des plateformes cloud fermées morcelle les données, crée une dépendance captive et compromet la souveraineté intellectuelle.

---

## 🛡️ La Solution : Arca-BrainOS

**Arca-BrainOS** est un système d'exploitation open-source et agentique pour **Obsidian** (et tout éditeur Markdown local). Il dote votre environnement de travail (terminal CLI, Claude Cowork, Gemini Spark) d'une flotte de **compétences autonomes (`Skill_arca-*.md`)** qui exécutent les corvées documentaires, maintiennent l'ontologie de votre savoir et pilotent vos sessions de Deep Work.

Le système articule harmonieusement deux dimensions de vos projets :
- **Les projets intellectuels & numériques :** Ingénierie logicielle, architecture de systèmes, recherche et rédaction.
- **Les projets d'action dans le monde réel :** Rénovation, préparation de vacances ou de randonnée itinerantes, suivi de santé/rééducation, pratique artistique.

Chaque projet est dynamiquement relié à vos **Domaines de vie (`3-Domaines-de-vie/`)** pour équilibrer votre énergie et nourrir vos rétrospectives saisonnières.

> 📜 **Philosophie & Vision :** Pour comprendre la mutation anthropologique, le *Pharmakon* de Stiegler et le refus des monopoles d'IA fermés, consultez **[Le Manifeste du Workflow Augmenté (MANIFESTO.fr.md)](MANIFESTO.fr.md)**.

<p align="center">
  <img src="assets/starter-vault-show-dont-tell.png" alt="Arca-BrainOS en action : Démonstration concrète de l'orchestration CLI et note Obsidian maillée" width="100%">
  <br>
  <em>Démonstration concrète : orchestration dans le terminal CLI à gauche, note Obsidian structurée et maillée aux cartes thématiques à droite.</em>
</p>

#### 🎯 Les 4 Piliers d'Arca-BrainOS :

- **📥 1. Ingestion & Distillation (Automatisée & Extensible) :** Capture et synthèse conceptuelle immédiate des flux bruts (articles web, vidéos, podcasts, notes vocales). Ce sas d'entrée est extensible via des connecteurs MCP (Model Context Protocol) selon vos propres outils : boîte email, messageries (WhatsApp, Telegram) ou gestionnaires de tâches.
- **🗂️ 2. Organisation & Maillage (Assistés) :** Gestion intelligente de vos notes : l'IA crée et entretient les liens pertinents entre vos notes (`[[...]]`), puis les rattache automatiquement à vos cartes thématiques et à vos Domaines de vie, sans aucun effort de classement manuel.
- **🚀 3. Deep Work & Exécution (Libération Humaine) :** Résumé de la session précédente, cadrage du focus actif (`arca-resume`), journalisation chronologique et mesure du gain de temps (`arca-close-session`).
- **🩺 4. Audit & Santé du Coffre (Supervisée) :** Diagnostic proactif des notes orphelines, réparation des liens brisés et exploration transversale (`arca-query`).

---

## ⚡ ROI Terrain Mesuré : Vitesse x4

Arca-BrainOS repose sur des **données empiriques réelles**, mesurées en continu sur 24 projets concrets et plus de 160 sessions de Deep Work :

| Métrique Clé | Résultat Mesuré | Impact Concret |
| :--- | :---: | :--- |
| **Multiplicateur de Vitesse** | **⚡ x4** | Vos projets avancent 4x plus vite |
| **Temps Net Économisé** | **🚀 +434 heures** | Plus de 10 semaines de travail intellectuel libérées |
| **Temps Réel Investi avec IA** | **152h** | Au lieu de ~587h de travail manuel estimé |

> 💡 **Contexte Réel :** Mesuré sur un coffre préexistant de plusieurs centaines de notes, et non sur un environnement démo vide.

---

## 💎 Principes Clés de Conception

1. **🔒 Souverain & Local-First :** Fichiers Markdown bruts (`.md`) sur votre disque. Zéro dépendance SaaS, propriété intégrale et pérenne de vos données.
2. **🤖 Runner & LLM-Agnostique :** Fonctionne aussi bien en ligne de commande (Google Antigravity, Claude Code, OpenCode) qu'avec des assistants de bureau connectés à vos fichiers locaux (Claude Cowork, Gemini Spark, Codex), ou des modèles 100% locaux sous Ollama. Changez d'outil à volonté sans friction.
3. **🧠 Mémoire Inter-Sessions Persistante :** Votre coffre devient la mémoire à long terme de l'agent IA, neutralisant l'amnésie entre les runs.
4. **🤝 Symbiose Non-Destructive :** L'IA gère l'intendance et enrichit le maillage. Elle n'altère ni ne réécrit jamais le style ou les contenus rédigés par l'humain.

<p align="center">
  <img src="assets/starter-vault-project-deep-work.png" alt="Cadrage de session Deep Work avec arca-resume et journal de bord automatisé dans Obsidian" width="100%">
  <br>
  <em>Cadrage cognitif de session avec arca-resume et journal de bord de projet automatisé directement dans Obsidian.</em>
</p>

---

## 📂 Architecture & Topographie du Vault

Arca-BrainOS repose sur une **architecture strictement découplée en deux parties** :

1. **Partie A : Le Moteur OS (`_Arca-BrainOS/`) :** Conteneur 100% portable regroupant les compétences (`skills/`), processus, modèles, registre d'architecture (`adr/`) et tests.
2. **Partie B : Votre Contenu Personnel (Coffre existant ou neuf) :** Vos notes et dossiers. Arca-BrainOS s'adapte à votre propre arborescence via les variables de sentiers configurables dans `AGENTS.md`.

```text
Votre-Coffre-Obsidian/
├── _Arca-BrainOS/                # 🧠 PARTIE A : Le Conteneur Moteur OS (100% Portable)
│   ├── AGENTS.md                 # Configuration système & variables de sentiers
│   ├── log.md                    # Journal d'audit chronologique (1 ligne / action)
│   ├── skills/                   # 🔌 Compétences Agentiques Modulaires (Skill_arca-*.md)
│   ├── process/                  # 📚 Fiches Méthodologiques (Process-*.md)
│   ├── templates/                # 📄 Modèles de Notes (Projet, Theme, Area, ADR)
│   ├── adr/                      # 📜 Registre des Décisions d'Architecture (ADR-001...)
│   └── tests/                    # 🧪 Banc d'Essai Agentique & Fixtures
│
├── Home.md                       # Cockpit Exécutif Optionnel (Inclus dans starter-vault)
├── 0-Inbox/                      # 🧠 PARTIE B : Vos Contenus 2nd Brain (Configurables)
├── 1-Projects/                   # Projets Actifs (P-...) & Incubation (_Incubation/)
├── 2-Ressources/                 # Base de Connaissances (Notes/, IA-generated/, Themes/)
├── 3-Domaines-de-vie/            # Domaines de responsabilité (Index README.md)
└── 4-Archives/                   # Projets Clôturés & Domaines Inactifs
```

---

## ⚡ Quickstart (Onboarding en 1 Minute)

> 💡 **Guide Opérationnel Détaillé :** Pour une visite guidée complète, consultez **[GETTING_STARTED.fr.md](GETTING_STARTED.fr.md)**.

### 1. Prérequis
* **[Obsidian](https://obsidian.md)** 
* **Un Assistant ou Runner IA :** En terminal local (**Google Antigravity**, **Claude Code**, **OpenCode**) ou en environnement de travail de bureau (**Claude Cowork**, **Gemini Spark**, **Codex**).
* *(Optionnel)* **[Dataview Plugin](https://github.com/blacksmithgu/obsidian-dataview)** : Requis uniquement si vous utilisez le cockpit visuel `Home.md`.

### 2. Installation (2 Options au Choix)

#### 📁 Option A : Ajouter à un coffre Obsidian EXISTANT
Copiez le dossier `starter-kit/fr/_Arca-BrainOS/` à la racine de votre coffre actuel. Lancez votre terminal IA et collez l'instruction :
```text
Lis https://github.com/Arca-Brain/Arca-BrainOS/blob/main/INSTALL.fr.md (ou INSTALL.fr.md local) et installe Arca-BrainOS pour moi.
```
*L'agent analyse vos sentiers, configure `AGENTS.md` et lance les vérifications sans modifier vos notes existantes.*

#### 📦 Option B : Démarrer de zéro avec un coffre prêt-à-l'emploi
Ouvrez directement le dossier `starter-kit/fr/starter-vault/` comme nouveau coffre dans Obsidian.
> 💡 Ouvrez la note d'accueil **`00-COMMENCER-ICI.md`** à la racine pour tester 3 premières commandes en 5 minutes.

### 3. Test de Vérification
Dans votre terminal IA, lancez :
```bash
arca-test
```
*L'agent exécute les assertions automatisées pour valider l'intégrité du système.*

---

## 📜 Licence Open-Source

Arca-BrainOS est un logiciel open-source libre et souverain publié sous **[Licence MIT](LICENSE)** (voir [`LICENSE.md`](LICENSE.md)).

Cette licence garantit une adoption sans friction, une compatibilité totale avec les environnements d'entreprise et l'assurance d'un bien commun préservé.

---

## 🙏 Remerciements & Inspirations

Arca-BrainOS s'appuie sur les travaux de **David Allen** (GTD), **Tiago Forte** (BASB & PARA), **Sönke Ahrens** (Zettelkasten), **Daniel Miessler** (PAI & architecture UNIX), **Bernard Stiegler** (Pharmakon), **Eliott Meunier** et la communauté **Obsidian**.

---

<p align="center">
  <i>Développé avec passion par Hugues & la communauté Arca-BrainOS.</i>
</p>
