---
Id: "202607172328"
category: Process
date-created: "2026-07-17"
tags:
  - process
  - audit
  - pkm
  - maintenance
  - ia
---
# Process : Audit de Santé & Maintenance du Vault

- **Fréquence** : Monthly / Saisonnière (Pratiqué lors des revues mensuelles ou en fin de trimestre).
- **Déclencheur** : Calendrier de maintenance mensuel ou constat de frictions dans le maillage du Second Cerveau.
- **Temps actuel** : ~1h / mois (vérification manuelle fastidieuse des liens cassés, recherche des orphelines).

---
## Input
* L'ensemble du coffre Obsidian (Vault).
* L'index central `_Arca-BrainOS/index.md` et la racine `Home.md`.

## Étapes
1. **Lancer le diagnostic de santé** : Invoquer la commande `arca-audit` pour scanner l'ensemble du coffre.
2. **Analyser les métriques de santé & de productivité** :
   - Calculer l'Indice de Santé PARA (ratio distillations / notes projets).
   - Consolider le Bilan Temporel & Productivité IA (projets actifs vs archivés : `sessions_count`, `total_real_duration`, `total_estimated_manual`, `total_time_saved`).
   - Détecter les notes orphelines (notes sans aucun lien entrant ni sortant).
   - Repérer les liens fantômes / brisés (`ghost links`).
   - Auditer le respect du frontmatter YAML strict et la propreté de `Home.md`.
3. **Réparer les frictions** :
   - Invoquer `link-audit` ou `vault-lint` pour corriger automatiquement ou proposer des corrections sur les liens fantômes.
   - Ancrer les notes orphelines dans leurs MOCs thématiques respectifs (`T-`).
4. **Mettre à jour l'index central** : Régénérer ou ré-indexer la structure dans `_Arca-BrainOS/index.md`.
5. **Archiver le diagnostic dans le journal central** : Consigner automatiquement le rapport horodaté et mettre à jour l'Executive Summary & Tendances Long Terme dans `_Arca-BrainOS/audit-log.md`.
6. **Journaliser l'action système** : Enregistrer une ligne d'action d'une seule ligne dans `_Arca-BrainOS/log.md`.

## Méthode & Critères de Qualité
* **Structure requise** : Un rapport d'audit transparent présenté dans le chat et automatiquement consigné dans `_Arca-BrainOS/audit-log.md`.
* **À faire absolument (DO)** :
  * Traiter en priorité les liens brisés qui coupent la navigation dans le graphe.
  * S'assurer qu'aucune note distillée ne reste orpheline de son MOC.
  * Consigner l'audit dans `_Arca-BrainOS/audit-log.md` avec la synthèse Executive Summary à jour.
* **À éviter absolument (DON'T)** :
  * Ne pas modifier massivement plus de 3 fichiers hors de `2-Ressources/IA-generated/` sans demander une confirmation explicite.
  * Ne pas supprimer de notes humaines sans autorisation explicite.

## Output
* Rapport d'audit de santé du Vault (Santé PARA, Tableau de Synthèse ROI Projets, Orphelines, Ghost Links).
* Fichier journal `_Arca-BrainOS/audit-log.md` mis à jour (Executive Summary + Entrée horodatée).
* Liens brisés réparés et notes orphelines maillées.
* Index central `index.md` à jour.

## 💡 Exemples Concrets d'Exécution & Prompts Types

### Cas 1 : Revue Mensuelle d'Hygiène & Diagnostic de Santé
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-audit` (ou dans le chat : *"Audite la santé globale de mon coffre"*).
- **État Initial :**
  Plusieurs dizaines de notes ont été créées au fil du mois, certaines sont orphelines, d'autres contiennent des liens brisés.
- **Orchestration Agentique (Compétence [[Skill_arca-audit]]) :**
  1. L'agent calcule l'indice de santé PARA (ratio notes distillées vs projets actifs).
  2. Il consolide les métriques de productivité et de temps économisé à travers tous les projets actifs et archivés.
  3. Il dresse la liste des notes isolées (sans lien entrant ni sortant) et des liens fantômes (`ghost links`).
  4. Il consigne le diagnostic dans `_Arca-BrainOS/audit-log.md` et ajoute une ligne unique dans `_Arca-BrainOS/log.md`.
- **État Final (Output) :**
  Un tableau de bord complet s'affiche dans le chat avec les actions de remédiation recommandées.

### Cas 2 : Réparation Ciblée des Liens Brisés
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Dans le chat : *"Répare les 2 liens fantômes détectés dans mon MOC T-PKM"*
- **Orchestration Agentique (Compétences [[Skill_arca-converge]] / `link-audit`) :**
  Proposition de réconciliation sémantique, confirmation humaine dans le chat, puis mise à jour sécurisée du fichier MOC.

### 🔗 Compétences Agentiques Associées
- [[Skill_arca-audit]] : Diagnostic de santé, détection des orphelines, ghost links et bilan ROI global.
- [[Skill_arca-converge]] : Ré-ancrage structurel des notes dans les Thèmes MOC (`T-`).
- [[Skill_arca-test-suite]] : Banc d'essai automatisé validant la conformité des règles système.

## Douleurs principales
* Dégradation progressive de la propreté du Second Cerveau ("entropie numérique").
* Perte de visibilité sur le ROI temporel global et l'impact de l'IA à travers le temps.

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Diagnostic & Métriques** | **Agent IA** | Commande `arca-audit` (Scan complet, détection orphelines, ghost links & consolidation ROI projets). | **Aucun** : Calcul automatique des métriques par l'IA. | 🟢 (Opérationnel) |
| **2. Présentation du rapport** | **Agent IA** | Synthèse claire des frictions et du tableau ROI projets dans le chat. | **Analyse** : Prendre connaissance du bilan de santé et de productivité. | 🟢 (Opérationnel) |
| **3. Correction des liens & Orphelines** | **Agent IA (Supervisé)** | Skills `link-audit`, `vault-lint` & maillage MOC. | **Validation** : Approuver les plans de correction (règle des 3 fichiers). | 🟢 (Opérationnel) |
| **4. Ré-indexation** | **Automatisation** | Mise à jour automatique de `index.md`. | **Contrôle** : Vérification de la cohérence de l'index. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Décision de suppression ou de conservation** : Seul l'humain décide si une note désuète doit être supprimée, archivée ou fusionnée.
* **Validation des grosses modifications** : Respect de la règle de sécurité (l'IA demande une confirmation explicite si > 3 fichiers modifiés hors `IA-generated/`).

**Pipeline complet** : `arca-audit` (Diagnostic Agent) $\rightarrow$ Rapport de santé $\rightarrow$ Validation du plan (Humain) $\rightarrow$ `link-audit` & Ré-indexation (Agent/Auto).
