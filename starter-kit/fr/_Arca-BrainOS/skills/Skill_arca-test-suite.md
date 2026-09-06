# 🛠️ Skill : arca-test-suite (Banc d'Essai & Non-Régression Agentique 100% Skills)

- **Processus de Référence :** [[Process-Test-et-Evaluation-Agentique]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-test` ou `arca-test-suite` (ou `test-suite`).

## Objectif
Tester et valider l'intégrité globale de l'ensemble des 13 compétences agentiques (`arca-*`) et de la structure d'Arca-BrainOS en exécutant une suite de 13 assertions automatisées sur les fichiers échantillons (`_Arca-BrainOS/tests/fixtures/`) sans polluer les véritables notes du coffre.

## Workflow d'Exécution Séquentiel

1. **Test 1 : Triage & Routage Inbox (`arca-inbox-process`)**
   - Assertion : Qualification exacte des catégories (`source` ➔ `arca-distill`, `idea` ➔ `arca-organize-idea`) et détection des doublons dans `log.md`.
   - Résultat : 🟢 PASS / 🔴 FAIL.

2. **Test 2 : Préservation Humaine & Typage (`arca-organize-idea`)**
   - Assertion : Conservation à 100% du texte source original dans `## 📝 Note Brute` et typage YAML sans altération du texte.
   - Résultat : 🟢 PASS / 🔴 FAIL.

3. **Test 3 : Orchestration Master Skill (`arca-distill`)**
   - Assertion : Enchaînement séquentiel propre des 4 étapes (`synthesize` ➔ `converge` ➔ `mv` ➔ `impact`).
   - Résultat : 🟢 PASS / 🔴 FAIL.

4. **Test 4 : Formatage YAML Strict & Sections (`arca-synthesize`)**
   - Assertion : Guillemets `" "` obligatoires sur les chaînes du frontmatter, `status: "#new"`, et présence des 5 sections de synthèse.
   - Résultat : 🟢 PASS / 🔴 FAIL.

5. **Test 5 : Garde-fous & Maillage (`arca-converge`)**
   - Assertion : Arrêt et confirmation interactive si > 3 fichiers modifiés hors `IA-generated/`, et absence de tag `#to-review`.
   - Résultat : 🟢 PASS / 🔴 FAIL.

6. **Test 6 : Interactivité & Respect du Style (`arca-impact`)**
   - Assertion : Aucune modification de projet (`P-`) ou note humaine sans accord explicite de l'utilisateur dans le chat.
   - Résultat : 🟢 PASS / 🔴 FAIL.

7. **Test 7 : Ingestion & Retranscription (`arca-youtube`)**
   - Assertion : Création des notes brutes sous `0-Inbox/Youtube/` et journalisation sur une ligne dans `log.md`.
   - Résultat : 🟢 PASS / 🔴 FAIL.

8. **Test 8 : RAG Conversationnel Sans Pollution (`arca-query`)**
   - Assertion : Mode 100% conversationnel, citation de wikilinks `[[...]]`, pas d'écriture dans `log.md` sans enregistrement d'une fiche.
   - Résultat : 🟢 PASS / 🔴 FAIL.

9. **Test 9 : Formatage Tableaux & ROI Projets (`arca-audit`)**
   - Assertion : Tableaux Markdown unindentés à la colonne 0 sans puces `- `, calcul des métriques et archivage dans `audit-log.md`.
   - Résultat : 🟢 PASS / 🔴 FAIL.

10. **Test 10 : Cadrage & Horodatage d'Ouverture (`arca-resume`)**
    - Assertion : Lecture des 2-3 dernières sessions, formulation du focus et injection du bloc temporaire dans le journal.
    - Résultat : 🟢 PASS / 🔴 FAIL.

11. **Test 11 : Clôture & Synchronisation ROI (`arca-close-session`)**
    - Assertion : Horodate de fin, calcul durée réelle vs sans IA, finalisation sans cases à cocher actives dans le journal et maj du YAML cumulé.
    - Résultat : 🟢 PASS / 🔴 FAIL.

12. **Test 12 : Création Directe, Chaînage & Validation (`arca-create-note`)**
    - Assertion : Support des alias direct (`create-project`, `create-theme`, `create-domaine`), validation humaine interactive avant écriture, proposition de chaînage des thèmes inexistants, scan de justification des domaines et typage exact YAML (`category`, `areas`).
    - Résultat : 🟢 PASS / 🔴 FAIL.

13. **Test 13 : Couverture Documentaire Globale (READMEs)**
    - Assertion : 100% des fichiers `Skill_arca-*.md`, `Template-*.md` et `Process-*.md` sont référencés dans `skills/README.md`, `templates/README.md`, `process/README.md` et `AGENTS.md`.
    - Résultat : 🟢 PASS / 🔴 FAIL.

---

## 📊 Format du Rapport de Sortie (Console Chat)

```markdown
# 🧪 Rapport d'Évaluation Agentique Arca-BrainOS (100% Skills Coverage)

| Test | Compétence / Scope | Assertion Qualité | Statut |
| :--- | :--- | :--- | :---: |
| **Test 1** | `arca-inbox-process` | Qualification `category` & Détection doublons | 🟢 PASS |
| **Test 2** | `arca-organize-idea` | Préservation 100% Raw Note & Style Humain | 🟢 PASS |
| **Test 3** | `arca-distill` | Orchestration 4 Étapes Master Skill | 🟢 PASS |
| **Test 4** | `arca-synthesize` | Formatage Frontmatter YAML (Guillemets `" "` & `#new`) | 🟢 PASS |
| **Test 5** | `arca-converge` | Garde-fou 3 Fichiers & Absence de `#to-review` | 🟢 PASS |
| **Test 6** | `arca-impact` | Interactivité & Validation avant écriture | 🟢 PASS |
| **Test 7** | `arca-youtube` | Création Inbox Youtube & Log Horodaté | 🟢 PASS |
| **Test 8** | `arca-query` | Mode RAG 100% Conversationnel Sans Pollution | 🟢 PASS |
| **Test 9** | `arca-audit` | Formatage Markdown Tableaux (Col 0) & Log Audit | 🟢 PASS |
| **Test 10** | `arca-resume` | Cadrage Cognitif & Init Journal Horodaté | 🟢 PASS |
| **Test 11** | `arca-close-session` | Calcul ROI IA, Bilan Journal & Maj Frontmatter | 🟢 PASS |
| **Test 12** | `arca-create-note` | Validation humaine, Chaînage thèmes & Scan justification | 🟢 PASS |
| **Test 13** | Documentation | Couverture 100% READMEs (`skills`, `templates`, `process`, `AGENTS`) | 🟢 PASS |

**Résultat Global :** 13 / 13 Tests Validés avec Succès 🚀 (Couverture : 100%)
```
