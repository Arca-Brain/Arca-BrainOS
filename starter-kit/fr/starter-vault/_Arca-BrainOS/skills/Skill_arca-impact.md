# 🛠️ Skill : arca-impact (Analyse d'Impact & Alignement Projets/Thèmes)

- **Processus de Référence :** [[Process-Ingestion-et-Distillation-de-Medias]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape `arca-impact` (ou `brain-impact`) suivi du lien ou du nom d'une note distillée (ex: `AI-Distil-[Nom].md`), ou lorsqu'il est invoqué automatiquement par le Master Skill `arca-distill`.

## Objectif
Analyser une note de synthèse récemment distillée pour identifier son impact potentiel sur les projets en cours (`/1-Projects/`) ou les thèmes (`/2-Ressources/Themes/`), formuler des recommandations stratégiques/tactiques sous forme interactive, et appliquer les modifications validées par l'utilisateur.

## Workflow d'Exécution Séquentiel

1. **Recherche de Contexte (Projets & Thèmes liés) :**
   - Scanne le dossier `1-Projects/` à la recherche des projets actifs (`P-[Nom].md`), des notes de leçons (`L-[Nom].md`) ou des fichiers thématiques (`T-[Nom].md`).
   - Parcourt le dossier `2-Ressources/Themes/` (racine et sous-dossiers thématiques `Theme [Nom]`).
   - Identifie les fichiers sémantiquement proches du sujet de la note distillée.

2. **Élaboration du Diagnostic d'Impact :**
   - Compare la nouvelle note distillée avec le contenu des projets/thèmes identifiés.
   - Formule des recommandations structurées selon 3 axes :
     - **💡 Alignement / Pivot Stratégique :** Comment cette nouvelle information influence la vision à long terme du projet ou du thème (ex: redéfinition des priorités).
     - **⚙️ Évolutions Tactiques / Actions :** Suggestions de nouvelles tâches (`- [ ]`) à insérer dans vos projets.
     - **🧠 Connaissances à intégrer :** Suggestions d'ajouts ou d'ajustements dans vos notes de cours ou leçons.

3. **Phase Interactive (Validation) :**
   - Présente le diagnostic de manière claire et structurée à l'utilisateur dans le chat.
   - Propose des choix d'actions précis (ex: *"Voulez-vous que j'ajoute la tâche [X] dans le projet [[P-Finance-Perso]] ?"* ou *"Souhaitez-vous intégrer cette leçon dans [[L-Strategie-Trinity]] ?"*).
   - **Règle absolue :** Attend le retour de l'utilisateur. Aucune modification de projet ou de thème humain ne doit être faite sans sa validation explicite dans le chat.

4. **Application & Journalisation :**
   - Applique chirurgicalement les modifications validées par l'utilisateur sur les projets/leçons (en respectant le style humain).
   - **Enregistrement de l'Impact :** Pour chaque action validée et appliquée sur un projet ou une leçon (ex: `[[P-Nom]]` ou `[[L-Nom]]`), écris une ligne récapitulative dans la section `## Application & Impact` de la note distillée source d'origine sous le format : `- [[P-Nom-Projet]] : Tâche "Description de la tâche" ajoutée le YYYY-MM-DD.` (si aucune action n'est validée, écris : `Aucune action directe planifiée à ce jour.`).
   - Ajoute une ligne de log dans `_Arca-BrainOS/log.md` :
     `[Date] - Impact analysé pour [[AI-Distil-...]] : [Nombre] modifications appliquées`
