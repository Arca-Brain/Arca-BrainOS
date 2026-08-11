---
date: 2026-08-09
title: "GETTING_STARTED.fr.md : Guide d'Onboarding Détaillé & Manuel Opérationnel (Arca-BrainOS)"
description: Guide opérationnel complet pour configurer DataviewJS, comprendre la méthodologie PARA adaptée, configurer les sentiers dans AGENTS.md, gérer les sessions Deep Work (arca-resume & arca-close-session) et utiliser les fiches de processus embarquées.
tags:
  - getting-started
  - onboarding
  - guide
  - obsidian
  - arca-brainos
status: "#completed"
---

# 🚀 GETTING STARTED : Guide d'Onboarding Détaillé & Manuel Opérationnel

🇬🇧 **[Read the English version (GETTING_STARTED.md)](GETTING_STARTED.md)**

Bienvenue sur **Arca-BrainOS** ! Ce guide complète les instructions rapides du **[README.fr.md](README.fr.md)** en fournissant des explications détaillées pour configurer votre environnement, appréhender l'architecture PARA adaptée, piloter vos sessions de Deep Work et exploiter les 7 fiches de processus embarquées.

---

## 🧠 1. Prérequis Conceptuels & Le Framework PARA Adapté

### A. Prérequis Conceptuel : Construire un Second Cerveau (BASB)
Bien que la compréhension de la méthode **Building a Second Brain (BASB)** de Tiago Forte ne soit **PAS requise pour installer physiquement le logiciel**, elle constitue un **prérequis conceptuel essentiel** pour tirer le meilleur parti d'Arca-BrainOS :

* **Pourquoi c'est fondamental :** Arca-BrainOS est articulé autour du **Système P.A.R.A** (Projets, Domaines, Ressources, Archives) et du **Framework C.O.D.E** (Capturer, Organiser, Distiller, Exécuter).
* **Alignement cognitif :** Comprendre la différence entre des projets actifs limités dans le temps et des domaines de responsabilité permanents garantit que vos agents IA orientent les informations avec précision sans encombrer votre coffre.

---

### B. Architecture PARA Détaillée & Topographie du Coffre
Arca-BrainOS adapte la structure PARA de Tiago Forte en une hiérarchie modulaire découplée. Voici la structure exacte, le rôle de chaque dossier et des exemples concrets de notes :

```text
Votre-Coffre-Obsidian/
├── 0-Inbox/                      # 📥 Zone de Capture & Ingestion Brute
│   └── Youtube/                  # Ingestion automatique des transcripts YouTube
├── 1-Projects/                   # 🚀 Projets Actifs (P-[Nom-Projet].md)
├── 2-Ressources/                 # 📚 Base de Connaissances Long Terme
│   ├── Notes/                    # ✍️ Notes Rédigées par l'Humain & Journal
│   ├── IA-generated/             # 🤖 Zone d'Écriture Exclusive IA (AI-Distil-...)
│   └── Themes/                   # 🗺️ Fiches Thèmes / MOCs (T-...)
├── 3-Domaines-de-vie/            # 🧠 Domaines de Responsabilité Permanents (Index README.md)
└── 4-Archives/                   # 📦 Projets Terminés & Contenus Inactifs
    ├── Projets/                  # Archives des Projets Finalisés
    └── Areas/                    # Archives des Domaines Inactifs
```

#### 📥 `0-Inbox/` (Zone de Capture & Ingestion)
- **Rôle :** Zone d'attente temporaire pour recueillir les idées brutes, captures web, notes de réunion et transcriptions YouTube avant traitement.
- **Règle :** Maintenu à "Inbox Zero" grâce aux compétences `arca-inbox-process` ou `arca-organize-idea`.
- **Exemples :** `0-Inbox/idee-brute-ia.md`, `0-Inbox/Youtube/transcript-video-karpathy.md`.

#### 🚀 `1-Projects/` (Projets Actifs)
- **Rôle :** Entreprises actives à court/moyen terme assorties d'objectifs, de jalons précis et d'une date de fin.
- **Convention :** Les notes suivent le format `P-[Nom-Projet].md` et utilisent `Template-Projet.md`.
- **Exemples :** `1-Projects/P-Arca-BrainOS.md`, `1-Projects/P-Camino-del-Norte.md`.

#### 📚 `2-Ressources/` (Base de Connaissances)
Divisé en 3 couches distinctes pour maintenir une séparation totale entre la réflexion humaine et le traitement par l'IA :
1. **`2-Ressources/Notes/` (Écriture Humaine) :** Vos réflexions personnelles, synthèses manuelles et notes de référence rédigées par vos soins.  
   *Exemples :* `Notes/Principes-du-Zettelkasten.md`, `Notes/Synthese-Reunion-2026.md`.
2. **`2-Ressources/IA-generated/` (Zone d'Écriture Exclusive IA) :** Conteneur isolé où les agents IA génèrent leurs synthèses conceptuelles (`AI-Distil-[Sujet].md`) et fiches de synthèse (`AI-Synthesis-...`).  
   *Exemples :* `IA-generated/AI-Distil-Hermes-Agent.md`, `IA-generated/AI-Synthesis-Workflow.md`.
3. **`2-Ressources/Themes/` (Fiches Thèmes / MOCs) :** Fiches d'indexation thématiques commençant par `T-` qui regroupent les liens wikilinks (`[[...]]`) par sujet.  
   *Exemples :* `Themes/T-Intelligence-Artificielle.md`, `Themes/T-PKM.md`.

#### 🧠 `3-Domaines-de-vie/` (Domaines de Responsabilité Permanents)
- **Rôle :** Domaines de vie permanents et standards de qualité continus sans date d'échéance.
- **Convention :** Indexés via `3-Domaines-de-vie/README.md` et cadrés par `Template-Area.md`.
- **Exemples :** `3-Domaines-de-vie/Creativite.md`, `3-Domaines-de-vie/Sante.md`, `3-Domaines-de-vie/Travail.md`.

#### 📦 `4-Archives/` (Contenus Archivés)
- **Rôle :** Stockage à froid des projets terminés et des domaines inactifs, préservant la mémoire historique.
- **Sous-dossiers :** `4-Archives/Projets/` et `4-Archives/Areas/`.

---

## ⚙️ 2. Configuration Détaillée de l'Environnement

### A. Configuration du Plugin Dataview (Crucial)
Arca-BrainOS alimente son cockpit exécutif (`Home.md`) et les widgets de focus par **DataviewJS**. Sans l'activation des requêtes JS, ces widgets ne s'afficheront pas.

1. Ouvrez Obsidian **Paramètres $\rightarrow$ Plugins communautaires**.
2. Installez et activez **Dataview**.
3. Dans les **Paramètres de Dataview**, vérifiez que :
   - ✅ **Enable JavaScript Queries** (`dataviewjs`) est **ACTIVÉ**.
   - ✅ **Enable Inline JavaScript Queries** est **ACTIVÉ**.

### B. Configuration des Sentiers Personnalisés dans `AGENTS.md`
Arca-BrainOS est 100% agnostique quant à l'organisation des dossiers. Le cœur du moteur réside dans `_Arca-BrainOS/`. Si votre coffre utilise des noms de dossiers spécifiques (ex: `Inbox/` au lieu de `0-Inbox/`), ajustez les variables d'en-tête dans `_Arca-BrainOS/AGENTS.md` :

```yaml
# 🌐 Topographie du Vault (Variables AGENTS.md)
PATH_INBOX: "0-Inbox/"
PATH_PROJECTS: "1-Projects/"
PATH_AREAS: "3-Domaines-de-vie/"
PATH_THEMES: "2-Ressources/Themes/"
PATH_IA_GENERATED: "2-Ressources/IA-generated/"
PATH_SYSTEM: "_Arca-BrainOS/"
```

### C. Ingestion Web avec l'Extension Officielle Obsidian Web Clipper
Pour capturer directement des articles, pages web et documentations depuis votre navigateur vers votre coffre sans aucune ressaisie :
1. Installez l'extension officielle **[Obsidian Web Clipper](https://obsidian.md/clipper)** (`https://obsidian.md/clipper`) sur votre navigateur (Chrome, Firefox, Safari, Brave).
2. Configurez le dossier de destination par défaut sur `0-Inbox/`.
3. Chaque page capturée est automatiquement formatée en Markdown propre avec métadonnées (`title`, `url`, `date`), prête à être qualifiée par `arca-inbox-process` ou distillée par `arca-distill`.

---

## 🪄 3. Protocole d'Installation (2 Options)

* **📁 Option A : Ajouter à un coffre EXISTANT (Dossier `_Arca-BrainOS/`)**  
  Copiez `_Arca-BrainOS/` à la racine de votre coffre actuel et lancez dans votre terminal IA :
  ```text
  Lis https://github.com/Arca-Brain/Arca-BrainOS/blob/main/INSTALL.fr.md (ou INSTALL.fr.md local) et installe Arca-BrainOS pour moi.
  ```
* **📦 Option B : Démarrer de zéro avec un coffre prêt-à-l'emploi (Dossier `starter-vault/`)**  
  Ouvrez directement le dossier `starter-vault/` dans Obsidian.  
  > 💡 **Conseil :** Renommez `starter-vault/` avec le nom de votre choix (`ArcaBrain`, `2ndBrain`, `MesNotes`) avant ou après l'ouverture !

---

## 🧪 4. Vérification du Coffre (`arca-test`)

Lancez le banc d'essai automatisé dans votre terminal IA pour vérifier la résolution des chemins et la validité des métadonnées :

```bash
arca-test
```

---

## 🪵 5. Pilotage des Sessions Deep Work (`arca-resume` & `arca-close-session`)

Arca-BrainOS introduit un protocole structuré en deux temps pour l'exécution des projets :

### Étape 1 : Cadrage Cognitif de Session (`arca-resume`)
Avant de démarrer une session de Deep Work sur une note projet (ex: `1-Projects/P-MonProjet.md`), tapez :

```bash
arca-resume 1-Projects/P-MonProjet.md
```

**Actions de votre co-pilote IA :**
1. Scanne les dernières entrées du journal de bord du projet.
2. Identifie le jalon actif et les tâches restantes.
3. Formule une **Intention de Session** ciblée (2 à 3 actions prioritaires).
4. Ouvre une entrée horodatée dans la section `## 🪵 Journal de Bord des Sessions` du projet et consigne l'événement dans `_Arca-BrainOS/log.md`.

### Étape 2 : Clôture de Session & Calcul du ROI (`arca-close-session`)
Lorsque vous terminez votre travail, tapez :

```bash
arca-close-session 1-Projects/P-MonProjet.md
```

**Actions de votre co-pilote IA :**
1. Fait le décompte des tâches accomplies et restantes.
2. Vous sollicite pour obtenir la durée réelle de la session.
3. Calcule le temps net économisé et le multiplicateur de vitesse.
4. Finalise l'entrée du journal dans la note projet et ajoute une ligne d'audit dans `_Arca-BrainOS/log.md`.

---

## 📚 6. Exploitation des Fiches Méthodologiques Embarquées (`process/`)

Pour comprendre la logique de chaque étape et guider votre co-pilote IA, appuyez-vous sur les 7 fiches de processus embarquées dans `_Arca-BrainOS/process/` :

* **`Process-Inbox-Clean-et-Dispatch.md`** : Qualification de l'inbox, nettoyage du YAML et tri.
* **`Process-Ingestion-et-Distillation-de-Medias.md`** : Synthèse des transcripts médias et ancrage dans les thèmes.
* **`Process-Exploration-Semantique-et-Recherche.md`** : RAG sémantique et ponts cognitifs.
* **`Process-Audit-et-Maintenance-du-Vault.md`** : Audit de santé PARA et détection des liens orphelins.
* **`Process-Pilotage-de-Projets-et-Deep-Work.md`** : Cadrage des sessions de travail et tenue du journal.
* **`Process-Capitalisation-et-Synthese-MOC.md`** : Ancrage des connaissances et mise à jour des Thèmes (`T-`).
* **`Process-Test-et-Evaluation-Agentique.md`** : Banc d'essai et assertions automatisées.

---

## 🔗 Liens Utiles & Références
* 📜 **[Le Manifeste Arca-BrainOS (MANIFESTO.fr.md)](MANIFESTO.fr.md)**
* 🪄 **[Prompt d'Installation (INSTALL.fr.md)](INSTALL.fr.md)**
* 🤝 **[Guide de Contribution (CONTRIBUTING.fr.md)](CONTRIBUTING.fr.md)**
* ⚖️ **[Licence Hybride (LICENSE.md)](LICENSE.md)**
