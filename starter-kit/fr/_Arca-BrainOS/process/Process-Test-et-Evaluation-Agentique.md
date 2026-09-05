# ⚙️ Processus : Test & Évaluation Agentique (Arca Test Suite)

## Métadonnées
- **ID :** `Process-Test-et-Evaluation-Agentique`
- **Titre :** Protocole d'Évaluation Non-Régression & Qualité Agentique Arca-BrainOS
- **Statut :** `🟢 Actif`
- **Fréquence :** À chaque refonte majeure des skills, mise à jour des prompts ou changement de modèle d'IA (LLM).
- **Responsable :** Humain + Agent Co-pilote (`arca-test`)

---

## 🎯 Objectif
Garantir la stabilité, l'absence de régression et le respect strict des garde-fous de sécurité du coffre Obsidian lors de la modification de n'importe laquelle des 11 compétences agentiques (`arca-*`) ou fiches de macro-processus.

---

## 🗂️ Matrice de Couverture des 12 Tests (100% Skills)

| Test # | Compétence Cible | Scénario & Assertion Qualité | Fixture / Support |
| :---: | :--- | :--- | :--- |
| **1** | `arca-inbox-process` | Qualification `category` (`source`/`idea`) & détection doublons | `test-raw-idea.md` |
| **2** | `arca-organize-idea` | Préservation à 100% de la Raw Note & typage YAML | `test-raw-idea.md` |
| **3** | `arca-distill` | Orchestration séquentielle 4 étapes Master Skill | `test-youtube-transcript.md` |
| **4** | `arca-synthesize` | Formatage YAML strict (Guillemets `" "` & `status: "#new"`) | `test-youtube-transcript.md` |
| **5** | `arca-converge` | Garde-fou de sécurité (> 3 fichiers modifiés) & MOC | `test-dummy-project.md` |
| **6** | `arca-impact` | Interactivité et validation explicite avant modification | `test-dummy-project.md` |
| **7** | `arca-youtube` | Création de fichier dans `0-Inbox/Youtube/` & log | Transcript URL |
| **8** | `arca-query` | RAG 100% conversationnel sans écriture non autorisée | Vault + Inbox |
| **9** | `arca-audit` | Tableaux Markdown col 0 (unindentés) & `audit-log.md` | Vault complet |
| **10** | `arca-resume` | Cadrage récent (2-3 sessions) & bloc temporaire horodaté | `test-dummy-project.md` |
| **11** | `arca-close-session` | Calcul ROI IA, bilan sans cases à cocher & maj YAML | `test-dummy-project.md` |
| **12** | Documentation | Couverture 100% des READMEs (`skills`, `process`, `AGENTS`) | Arborescence `_Arca-BrainOS/` |

---

## 🛠️ Protocole d'Exécution (`arca-test`)

1. **Lancement :** Tape la commande `arca-test` ou `arca-test-suite` dans le chat.
2. **Exécution isolée :** L'agent déroule les 12 assertions sur le dossier `_Arca-BrainOS/tests/fixtures/`.
3. **Rapport Flash :** L'agent restitue le tableau de bord avec le taux de réussite (cible : **12/12 PASS**).

---

## 💡 Exemples Concrets d'Exécution & Prompts Types

### Cas 1 : Lancement de la Batterie de Tests de Non-Régression
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-test` (ou `arca-test-suite`).
- **Orchestration Agentique (Compétence [[Skill_arca-test-suite]]) :**
  L'agent parcourt les 12 assertions automatisées sur les fixtures de test (`test-raw-idea.md`, `test-youtube-transcript.md`, `test-dummy-project.md`) sans altérer les vraies notes du coffre.
- **Résultat Attendu (Output) :**
  Tableau récapitulatif dans le chat affichant **12/12 PASSED (100% de couverture)** garantissant la solidité et l'intégrité de l'OS.

### 🔗 Compétences Agentiques Associées
- [[Skill_arca-test-suite]] : Banc d'essai automatisé et validation continue.
