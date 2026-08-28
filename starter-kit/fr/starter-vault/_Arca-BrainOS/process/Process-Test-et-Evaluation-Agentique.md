# ⚙️ Processus : Test & Évaluation Agentique (Arca Test Suite)

## Métadonnées
- **ID :** `Process-Test-et-Evaluation-Agentique`
- **Titre :** Protocole d'Évaluation Non-Régression & Qualité Agentique Arca-BrainOS
- **Statut :** `🟢 Actif`
- **Fréquence :** À chaque refonte majeure des skills, mise à jour des prompts ou changement de modèle d'IA (LLM).
- **Responsable :** Humain + Agent Co-pilote (`arca-test`)

---

## 🎯 Objectif
Garantir la stabilité, l'absence de régression et le respect strict des garde-fous de sécurité du coffre Obsidian lors de la modification de n'importe laquelle des compétences agentiques (`arca-*`) ou fiches de macro-processus.

---

## 🗂️ Matrice de Couverture des 13 Tests (100% Skills)

| Test # | Compétence Cible | Scénario & Assertion Qualité | Fixture / Support |
| :---: | :--- | :--- | :--- |
| **1** | `arca-inbox-process` | Qualification `category` (`source`/`idea`) & détection doublons | `test-raw-idea.md` |
| **2** | `arca-organize-idea` | Préservation à 100% de la Note Brute & typage YAML | `test-raw-idea.md` |
| **3** | `arca-distill` | Orchestration séquentielle 4 étapes Master Skill | `test-youtube-transcript.md` |
| **4** | `arca-synthesize` | Formatage YAML strict (Guillemets `" "` & `status: "#new"`) | `test-youtube-transcript.md` |
| **5** | `arca-converge` | Garde-fou de sécurité (> 3 fichiers modifiés) & MOC | `test-dummy-project.md` |
| **6** | `arca-impact` | Interactivité et validation explicite avant modification | `test-dummy-project.md` |
| **7** | `arca-youtube` | Création de fichier dans `0-Inbox/Youtube/` & log | Transcript URL |
| **8** | `arca-query` | RAG 100% conversationnel sans écriture non autorisée | Vault + Inbox |
| **9** | `arca-audit` | Tableaux Markdown col 0 (unindentés) & `audit-log.md` | Vault complet |
| **10** | `arca-resume` | Cadrage récent (2-3 sessions) & bloc temporaire horodaté | `test-dummy-project.md` |
| **11** | `arca-close-session` | Calcul ROI IA, bilan sans cases à cocher & maj YAML | `test-dummy-project.md` |
| **12** | `arca-create-note` | Typage YAML (`category`, `areas`) & Routage Alias | Standard templates |
| **13** | Documentation | Couverture 100% des READMEs (`skills`, `templates`, `process`, `AGENTS`) | Arborescence `_Arca-BrainOS/` |

---

## 🛠️ Protocole d'Exécution (`arca-test`)

1. **Lancement :** Tape la commande `arca-test` ou `arca-test-suite` dans le chat.
2. **Exécution isolée :** L'agent déroule les 13 assertions sur le dossier `_Arca-BrainOS/tests/fixtures/`.
3. **Rapport Flash :** L'agent restitue le tableau de bord avec le taux de réussite (cible : **13/13 PASS**).
