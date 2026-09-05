# 🛠️ Skill : arca-synthesize (Synthèse & Distillation)

- **Processus de Référence :** [[Process-Ingestion-et-Distillation-de-Medias]]

## Déclencheur
Invoqué soit par l'utilisateur (`arca-synthesize [fichier]` / `brain-synthesize`), soit appelé automatiquement par le Master Skill `arca-distill`.

## Workflow d'Exécution
1. **Analyse & Merge :** Analyse la source. Cherche dans `2-Ressources/IA-generated/` si une fusion avec une note `AI-Distil-` existante est pertinente.
2. **Création/Mise à jour :** Rédige la synthèse dans `2-Ressources/IA-generated/` avec le préfixe `AI-Distil-`.
3. **Journalisation :** Ajoute une seule ligne dans `_Arca-BrainOS/log.md` sous le format : `[Date] - Action IA (Synthèse) : [[Nom-de-la-Note]]`.

## Formatage Strict de la Note "AI-Distil"

***RÈGLE YAML STRICTE :*** Utilise exclusivement des guillemets doubles `" "` pour TOUTES les valeurs textuelles du frontmatter. N'utilise jamais de caractères `:` ou `-` à l'intérieur des valeurs sans guillemets. Le champ `status` doit impérativement être `#new`.

La note générée doit OBLIGATOIREMENT suivre cette structure :

---
date: "YYYY-MM-DD"
title: "Titre clair"
description: "Résumé d'une phrase"
tags: [ai-generated, theme/...]
status: "#new"
---

## Résumé Synthétique
Un paragraphe fusionnant tous les apports de la source.

## Le Noyau 
- **Ideas :** Les idées forces et intuitions majeures.
- **Beliefs :** Postulats de l'auteur et points de vue.
- **Models :** Mécanismes théoriques et grilles de lecture.
- **Strategies :** Actions concrètes et recommandations.

## Application & Impact
(Traces des projets influencés ou des tâches planifiées à la suite de cette note).

## Connexions Suggérées
(Liens vers les notes P-, L- ou T- pertinentes du Vault).

### Consigne de recherche des connexions :
- Scanne activement le Vault pour identifier les notes pertinentes à proposer.
- Cherche les correspondances thématiques ou de projets dans `2-Ressources/Themes/` (racine et sous-dossiers thématiques) ainsi que dans `1-Projects/` (notamment les notes de projet `P-` et les thèmes `T-` s'y trouvant).

## Historique des Sources
- [[Lien-vers-la-source-1]]
