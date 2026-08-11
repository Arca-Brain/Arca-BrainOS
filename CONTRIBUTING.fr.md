---
date: 2026-08-09
title: "CONTRIBUTING.fr.md : Guide de Contribution à Arca-BrainOS"
description: Directives officielles de contribution pour la création de compétences agentiques, fiches de processus méthodologiques, playbooks et maintien de la conformité du banc de test.
tags:
  - contributing
  - open-source
  - guidelines
  - developer
  - arca-brainos
status: "#completed"
---

# 🤝 CONTRIBUTING : Contribuer à Arca-BrainOS

🇬🇧 **[Read the English version (CONTRIBUTING.md)](CONTRIBUTING.md)**

Merci de votre intérêt pour contribuer à **Arca-BrainOS** !

Arca-BrainOS est conçu comme un **"Objet Technique Ouvert" au sens de Simondon** : un système transparent, modulaire et extensible construit par et pour les penseurs, bâtisseurs et professionnels de la connaissance. Nous accueillons avec enthousiasme les contributions qui enrichissent les compétences, affinent les fiches méthodologiques ou améliorent la santé du coffre.

---

## 🎯 1. Types de Contributions Bienvenues

Vous pouvez contribuer à Arca-BrainOS de plusieurs façons :

1. **🔌 Nouvelles Compétences Agentiques (`Skill_arca-*.md`)** : Création de compétences modulaires stockées dans `_Arca-BrainOS/skills/` pour automatiser des flux spécifiques de recherche, d'organisation ou d'analyse.
2. **📚 Fiches Méthodologiques de Processus (`Process-*.md`)** : Rédaction de guides de processus mixte humain/IA stockés dans `_Arca-BrainOS/process/`.
3. **📘 Playbooks Opérationnels (`Playbook-*.md`)** : Conception de guides d'enablement étape-par-étape stockés dans `_Arca-BrainOS/playbooks/`.
4. **🧪 Assertions pour le Banc de Test (`_Arca-BrainOS/tests/`)** : Ajout d'assertions et de jeux d'essai (fixtures) dans `Skill_arca-test-suite.md` pour prévenir les régressions.
5. **🐛 Corrections de Bugs & Documentation** : Clarification des guides, traduction, ou correction de la gestion des sentiers.

---

## 📏 2. Directives Architecturales & Conventions

Lors de la création ou de la modification de composants, veillez au respect strict de ces garde-fous :

### A. Sentiers Agnostiques de Dossiers
Ne saisissez jamais de chemins absolus ni de répertoires locaux figés dans les compétences. Référez-vous toujours aux variables de sentiers canoniques définies dans `AGENTS.md` :

```yaml
PATH_INBOX: "0-Inbox/"
PATH_PROJECTS: "1-Projects/"
PATH_AREAS: "3-Domaines-de-vie/"
PATH_THEMES: "2-Ressources/Themes/"
PATH_IA_GENERATED: "2-Ressources/IA-generated/"
PATH_SYSTEM: "_Arca-BrainOS/"
```

### B. Préservation du Style Humain (Règle 2)
Les compétences agentiques ne doivent **jamais** effacer, réécrire ou modifier en aveugle le contenu rédigé par l'humain dans les notes projets (`P-`), leçons (`L-`) ou domaines (`3-Domaines-de-vie/`). Elles peuvent uniquement suggérer des wikilinks (`[[...]]`), mettre à jour les cases à cocher (`- [ ]`), ou ajouter des entrées de journal de bord.

### C. Maintien Inconditionnel des READMEs (Règle 4)
Tout ajout, création ou renommage d'une compétence (`Skill_arca-*.md`), fiche process (`Process-*.md`) ou playbook (`Playbook-*.md`) **DOIT** s'accompagner de la mise à jour immédiate :
1. Du README du dossier parent (`skills/README.md`, `process/README.md`, ou `playbooks/README.md`).
2. De l'index central de gouvernance [`AGENTS.md`](AGENTS.md).

### D. Règle de Ponctuation (Règle 5)
N'utilisez jamais de tiret cadratin (`—`) dans les notes ou documentations rédigées. Remplacez systématiquement cette ponctuation par des deux-points (`:`), des virgules (`,`), des points (`.`) ou des parenthèses `()`.

---

## 🧪 3. Tests & Validation (`arca-test`)

Avant de soumettre une Pull Request, vérifiez que votre contribution n'entraîne aucune régression :

1. Ajoutez les jeux d'essai ou assertions correspondantes dans `_Arca-BrainOS/skills/Skill_arca-test-suite.md`.
2. Exécutez le banc de test dans votre terminal IA :
   ```bash
   arca-test
   ```
3. S'assurer que toutes les assertions de qualité passent (`PASS`).

---

## 📥 4. Procédure de Pull Request (PR)

1. **Forker le Dépôt :** Créez votre propre fork d'[Arca-BrainOS sur GitHub](https://github.com/Arca-Brain/Arca-BrainOS).
2. **Créer une Branche :**
   ```bash
   git checkout -b feature/ma-nouvelle-competence
   ```
3. **Committer vos Changements :** Conservez des commits clairs et descriptifs :
   ```bash
   git commit -m "feat(skills): ajout du skill arca-web-capture et mise a jour de l'index"
   ```
4. **Pousser et Ouvrir la PR :** Poussez votre branche sur GitHub et ouvrez une Pull Request vers la branche `main` d'Arca-BrainOS.

---

## 📜 5. Cadre de Licence & Attribution des Contributions

Afin d'assurer des relations claires et transparentes avec la communauté des contributeurs open-source, toute soumission de Pull Request est régie par les règles suivantes :

1. **Attribution & Reconnaissance Publique :** Chaque contributeur conserve son droit d'auteur original et sera **publicment crédité** dans l'historique des commits GitHub, les métriques du dépôt et les notes de release officielles.
2. **Cession d'Usage Contributeur :** En soumettant une Pull Request à Arca-BrainOS, vous accordez à Hugues (auteur original) une licence non exclusive, perpétuelle, mondiale et libre de droits pour intégrer, modifier, distribuer et valoriser votre contribution au sein de l'écosystème Arca-BrainOS (incluant le dépôt open-source et les kits Pro officiels).
3. **Alignement Licence Hybride :**
   - Les compétences, scripts et code sont contribués sous **GNU AGPLv3**.
   - Les playbooks, fiches de processus et guides sont contribués sous **CC BY-NC-SA 4.0**.

---

<p align="center">
  <i>Merci de participer à la construction d'un avenir souverain et agentique pour la pensée humaine !</i>
</p>
