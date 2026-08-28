# 🛠️ Skill : arca-audit (Maintenance, Santé du Vault & Bilan Temporel)

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-audit` (ou `audit` / `brain-audit`).

## Objectif
Scanner la structure pour détecter les frictions, les notes isolées, maintenir l'intégrité du maillage (Inbox, MOCs, `IA-generated/`) et établir le bilan de productivité temporelle et ROI IA des projets (actifs et archivés).

## Workflow d'Exécution Séquentiel

1. **Calcul du Ratio d'Impact (Indice de Santé PARA) :**
   - Scanne le dossier `2-Ressources/IA-generated/` pour répertorier toutes les notes `AI-Distil-`.
   - Analyse la section `## Application & Impact` de chaque note.
   - Calcule le pourcentage de fiches liées à un projet (`[[P-` ou `[[T-` situé dans `1-Projects/`) par rapport au total.
   - Si le taux de notes "sans impact" dépasse 35 %, ajoute une alerte contre le piège de la "Collector's Fallacy" (l'illusion de l'accumulation).

2. **Détection des Notes Orphelines (Inbox & IA-generated) :**
   - Scanne `0-Inbox/Youtube/` et `2-Ressources/IA-generated/`.
   - Identifie les notes qui ne sont listées dans *aucun* fichier thématique `T-` (MOC) ou depuis `Home.md`.

3. **Analyse des Liens Brisés (Ghost Links) :**
   - Repère les syntaxes `[[Fichier-Inexistant]]` au sein des notes distillées récentes.
   - Liste ces "concepts fantômes" qui mériteraient la création d'une note dédiée ou d'un MOC.

4. **Vérification de la cohérence de la Documentation & READMEs (Coverage Check) :**
   - Scanne tous les fichiers `Skill_arca-*.md` dans `skills/` et `Process-*.md` dans `process/`.
   - Vérifie si chaque fichier est bien référencé sous forme de wikilink `[[...]]` dans `skills/README.md` et `process/README.md` respectifs ainsi que dans `AGENTS.md`.
   - En cas de fichier omis, lève une alerte `🚨 Oubli de Documentation : [Nom-du-fichier]` dans le rapport d'audit.
   - S'assure que les derniers fichiers créés dans `2-Ressources/IA-generated/` sont bien répertoriés dans `_Arca-BrainOS/log.md` et accessibles via la structure de `Home.md`.

5. **Consolidation & Bilan Temporel des Projets (Actifs & Archivés) :**
   - Scanne tous les fichiers projets dans `1-Projects/` (projets actifs) et `4-Archives/Projets/` (projets archivés).
   - Extrait les métadonnées frontmatter YAML de chaque note projet : `sessions_count`, `total_real_duration`, `total_estimated_manual`, `total_time_saved`.
   - Calcule la somme globale des sessions, du temps réel (Deep Work + IA), du temps estimé sans IA, du gain de temps net et du multiplicateur global de vitesse (ROI IA).

6. **Journalisation & Archivage de l'Audit dans `_Arca-BrainOS/audit-log.md` :**
   - Ouvre le fichier journal central `_Arca-BrainOS/audit-log.md`.
   - Met à jour les métadonnées frontmatter YAML (`last_update: "YYYY-MM-DD HH:mm"`, incrémente `total_audits`).
   - Met à jour la section `# 📊 Executive Summary & Tendances Long Terme` au sommet du fichier.
   - Insère le rapport d'audit complet horodaté `### 📅 Audit du [AAAA-MM-JJ HH:mm]` au sommet de la section `# 🪵 Historique Chronologique des Audits`.
   - Enregistre une trace d'exécution d'une seule ligne dans `_Arca-BrainOS/log.md` : `[YYYY-MM-DD HH:mm] arca-audit -> Diagnostic de santé & mise à jour du journal audit-log.md`.

## Format de Sortie (Tableau de Bord)
L'Agent affiche le résultat directement dans la console Antigravity sous forme de Rapport Flash :
- **📊 Ratio d'Impact :** [Pourcentage]% de notes appliquées à un projet (Cible : > 65%) [Alerte si dérive]
- **⏱️ Bilan Temporel & Productivité Globale des Projets :**

| Catégorie | Projets | Sessions | Temps Réel | Estimé Sans IA | Gain de Temps | Vitesse |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 🟢 **Actifs** | [N_actifs] | [S_actifs] | [T_réel_actifs] | [T_sans_ia_actifs] | 🚀 **+[Gain_actifs]** | **x[Speed_actifs]** |
| 📦 **Archivés** | [N_arch] | [S_arch] | [T_réel_arch] | [T_sans_ia_arch] | 🚀 **+[Gain_arch]** | **x[Speed_arch]** |
| 🏁 **TOTAL** | **[N_total]** | **[S_total]** | **[T_réel_total]** | **[T_sans_ia_total]** | 🚀 **+[Gain_total]** | **x[Speed_total]** |

- **🚨 Notes Isolées :** [Liste des notes sans MOC]
- **👻 Concepts Fantômes :** [Liens pointant vers le vide]
- **💡 Pistes d'Amélioration :** [Suggestions de regroupements thématiques ou de passerelles manquantes]
- **💾 Archivage :** ✅ Rapport consigné avec succès dans `/_Arca-BrainOS/audit-log.md`.
