---
Id: "202607172329"
category: Process
date-created: "2026-07-17"
tags:
  - process
  - capitalisation
  - moc
  - pkm
  - ia
---
# Process : Capitalisation Inter-Projets & Synthèse MOC

- **Fréquence** : Monthly / On Milestone (À l'issue de jalons majeurs de projets).
- **Déclencheur** : Fin d'un projet, atteinte d'une milestone clé, ou récurrence de principes transversaux dans plusieurs projets.
- **Temps actuel** : ~2h par projet (savoir confiné dans les projets terminés sans réutilisation globale).

---
## Input
* Notes de projets `P-` terminées ou jalons validés dans `1-Projects/`.
* Notes de connaissances ou retours d'expérience isolés.
* Cartes de Contenu thématiques (`T-`) situées dans `2-Ressources/Themes/` (racine et sous-dossiers thématiques).

## Étapes
1. **Analyser le patrimoine de connaissances** : Scanner le dossier `1-Projects/` pour identifier les enseignements clés et les livrables d'impact.
2. **Exécuter la synthèse transversale** : Invoquer les skills `compound` ou `knowledge` pour analyser les récurrences d'idées entre plusieurs projets et rédiger une note de synthèse transversale dans `2-Ressources/IA-generated/` ou `2-Ressources/`.
3. **Mettre à jour les MOCs** : Invoquer `moc-update` pour rattacher les nouvelles synthèses et notes de connaissances aux Cartes de Contenu `T-` pertinentes.
4. **Ancrer la connaissance** : Mettre à jour l'index central `_Arca-BrainOS/index.md` pour refléter la nouvelle structure MOC.
5. **Journaliser l'action** : Enregistrer une ligne de log dans `_Arca-BrainOS/log.md`.

## Méthode & Critères de Qualité
* **Structure requise** : La note de capitalisation doit extraire les principes généraux (méthode, architecture, pièges à éviter) indépendamment du contexte projet spécifique.
* **À faire absolument (DO)** :
  * Transformer le savoir contextuel (lié à un projet unique) en savoir réutilisable (pour de futurs projets).
  * Conserver la traçabilité vers les projets d'origine.
* **À éviter absolument (DON'T)** :
  * Ne pas dupliquer des connaissances déjà présentes dans un MOC sans consolidation.
  * Ne pas effacer le récit ou les notes personnelles de l'utilisateur.

## Output
* Note de synthèse transversale (`AI-Synthesis-` ou `Engineering/`).
* Cartes de Contenu (`T-`) mises à jour avec les nouveaux principes consolidés.
* Réseau de liens `cross-linker` enrichi.

## 💡 Exemples Concrets d'Exécution & Prompts Types

### Cas 1 : Synthèse Transversale d'Enseignements Projets
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : *"Analyse mes projets terminés et extrait les règles d'or méthodologiques dans une note de synthèse"* (mobilise `compound` / `knowledge`).
- **État Initial :**
  Plusieurs projets d'écriture ou d'infrastructure contiennent des apprentissages ou des retours d'expérience isolés dans leurs journaux de bord.
- **Orchestration Agentique :**
  1. L'agent scanne les sections `## 🪵 Journal de Bord des Sessions` et les notes liées.
  2. Il extrait les principes directeurs universels (indépendants du projet spécifique).
  3. Il rédige une fiche consolidée `AI-Synthesis-[Sujet].md` dans `2-Ressources/IA-generated/` ou `2-Ressources/Notes/`.
- **État Final (Output) :**
  La connaissance contextuelle est transformée en actif intellectuel pérenne réutilisable.

### Cas 2 : Enrichissement & Restructuration d'un Thème MOC
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : *"Mets à jour le MOC 2-Ressources/Themes/T-PKM.md avec les dernières distillations"* (mobilise `moc-update` / `arca-converge`).
- **Orchestration Agentique (Compétence [[Skill_arca-converge]]) :**
  L'agent ajoute les nouveaux liens conceptuels dans la bonne sous-section du Thème sans altérer les annotations manuelles rédigées par l'humain.

### 🔗 Compétences Agentiques Associées
- [[Skill_arca-converge]] : Ancrage de notes dans les MOCs thématiques (`T-`).
- [[Skill_arca-create-note]] : Création et instanciation de nouvelles fiches Thèmes MOC (`create-theme`).
- [[Skill_arca-close-session]] : Captation des apprentissages clés en fin de session de Deep Work.

## Douleurs principales
* "Réinventer la roue" à chaque nouveau projet faute d'avoir extrait les enseignements des projets passés.
* Connaissances précieuses enterrées dans des projets archivés et oubliées.

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Détection du savoir réutilisable** | **Agent + Humain** | Skill `compound` / `knowledge` (Scan des projets & notes de connaissances). | **Intention** : Identifier quelle expérience mérite d'être capitalisée. | 🟢 (Opérationnel) |
| **2. Synthèse transversale** | **Agent IA** | Génération de la note de synthèse croisée. | **Validation** : Relire et valider la fidélité des principes. | 🟢 (Opérationnel) |
| **3. Cross-linking & MOC Update** | **Automatisation** | Skills `cross-linker` et `moc-update`. | **Surveillance** : Ancrage propre dans la structure globale. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Discernement de la valeur à long terme** : L'IA suggère des recoupements, mais l'humain tranche sur ce qui constitue une vraie règle d'excellence personnelle.
* **Consolidation dans la vision d'avenir** : L'humain décide si ce savoir modifie les objectifs ou les standards futurs de ses Areas.

**Pipeline complet** : Projets `P-` / Notes de connaissances $\rightarrow$ `compound` (Agent IA) $\rightarrow$ Synthèse croisée $\rightarrow$ `cross-linker` & `moc-update` (Auto).
