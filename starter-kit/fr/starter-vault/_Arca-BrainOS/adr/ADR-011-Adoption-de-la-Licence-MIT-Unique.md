---
date: "2026-10-02"
title: "ADR-011 : Adoption de la Licence Open-Source MIT Unique"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - legal
target: "[[P-Projet-Alpha]]"
---

# 📜 ADR-011 : Adoption de la Licence Open-Source MIT Unique

---

## 1. Contexte & Problématique
Lors de la release v1.0.0-MVP, Arca-BrainOS avait adopté un modèle de double licence hybride : le code et les compétences (`skills/`) étaient sous licence GNU AGPLv3, tandis que les playbooks, la documentation et le manifeste étaient sous licence Creative Commons CC BY-NC-SA 4.0.

Ce choix initial visait à protéger le projet contre la captation commerciale par des éditeurs tiers (revente de kits fermés ou exploitation SaaS non redistribuée). Toutefois, l'expérience terrain et les retours d'adoption ont mis en évidence plusieurs frictions majeures :
1. **La phobie corporate de l'AGPLv3 :** Dans les grands groupes et les environnements d'entreprise, les équipes juridiques et de sécurité proscrivent l'AGPLv3 en raison des craintes de contamination virale de leur propriété intellectuelle. Cela constitue un verrou psychologique pour les salariés et décideurs désireux d'expérimenter Arca-BrainOS sur leur poste professionnel.
2. **La friction cognitive de la double licence :** La superposition de deux licences distinctes complique la compréhension des droits accordés et freine les contributions communautaires.
3. **La cohérence avec le Manifeste et l'éthique du projet :** Le positionnement d'Arca-BrainOS milite pour l'émancipation face aux monopoles de l'information et pour la sanctuarisation de la pensée dans un format ouvert. Restreindre l'usage de la documentation via une clause Non-Commerciale entrait en tension avec la mission de diffusion d'un bien commun universel.

---

## 2. Décision Retenue
Arca-BrainOS abandonne intégralement le modèle de double licence hybride (AGPLv3 + CC BY-NC-SA 4.0) au profit d'une **licence unique et universelle MIT**.

Désormais, l'ensemble du dépôt public `Arca-Brain/Arca-BrainOS` (code, scripts, compétences agentiques, fiches process, playbooks, templates et documentation) est distribué sous licence MIT.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - **Adoption sans friction :** Standard universel de facto sur GitHub, dans l'écosystème Obsidian et dans l'univers des agents CLI.
  - **Compatibilité d'entreprise totale :** Neutralisation immédiate des blocages juridiques (compatible grands groupes, ETI et indépendants).
  - **Clarté juridique absolue :** Un seul fichier `LICENSE` de 15 lignes, un badge vert `License: MIT`, zéro ambiguïté pour les utilisateurs et contributeurs.
  - **Plein alignement idéologique :** Renforcement de la légitimité d'Arca-BrainOS en tant que standard libre et ouvert pour un système d'exploitation cognitif personnel souverain.
- **Compromis & Contraintes assumés :**
  - **Autorisation de réutilisation commerciale par des tiers :** Une entité tierce peut légalement intégrer ou redistribuer des composants du système. Ce risque est jugé marginal et assumé, car l'adhésion dépend du flux continu d'améliorations, de la crédibilité de la marque et de l'accompagnement humain.

---

## 4. Alternatives Écartées
- **Maintien du modèle Hybride (AGPLv3 + CC BY-NC-SA 4.0) :** Écarté car il pénalise l'adoption en entreprise et contredit l'esprit d'ouverture radicale promu par le manifeste.
- **Licence Apache 2.0 :** Envisagée pour sa clause expresse sur les marques et brevets, mais jugée moins immédiatement lisible et populaire que le standard MIT pour un coffre centré sur le Markdown.
- **GPLv3 unifiée :** Écartée car elle maintient un copyleft perçu comme trop restrictif par les directions informatiques de grandes entreprises.

---

## 5. Références & Liens
- Projet Maître : [[P-Projet-Alpha]]
- Fichiers de référence : `LICENSE`, `LICENSE.md`, `README.md`, `README.fr.md`, `CONTRIBUTING.md`, `CONTRIBUTING.fr.md`
