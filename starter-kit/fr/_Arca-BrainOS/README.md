# 🧠 Moteur Cognitif Arca-BrainOS

> *Bienvenue dans le cœur du Second Cerveau Arca-BrainOS. Ce répertoire contient l'intégralité de l'infrastructure logicielle, des compétences agentiques, des fiches de processus, des modèles, des mémoires et des journaux système.*

---

### 📂 Architecture des Sous-Dossiers

- **`[[_Arca-BrainOS/skills/README|skills/]]`** : *Compétences Agentiques*
  Contient l'ensemble des workflows exécutables par l'IA (`Skill_arca-*.md`) pour l'inbox, la distillation, l'audit et le Deep Work.
- **`[[_Arca-BrainOS/process/README|process/]]`** : *Fiches de Macro-Processus*
  Contient la documentation des processus de pensée et les matrices de répartition des rôles Humain/IA.
- **`[[_Arca-BrainOS/templates/README|templates/]]`** : *Modèles de Notes Obsidian*
  Contient les gabarits normalisés pour les projets, les processus, les idées et les journaux.
- **`[[_Arca-BrainOS/scripts/README|scripts/]]`** : *Scripts & Registres Automatisés*
  Contient les scripts shell (ingestion YouTube) et leurs registres de dédoublonnage.
- **`[[_Arca-BrainOS/adr/README|adr/]]`** : *Architecture Decision Records*
  Registre officiel des décisions architecturales et arbitrages structurants (ADR-001 à ADR-011).
- **`tests/`** : *Banc d'Essai Agentique & Fixtures*
  Contient les jeux de test (`fixtures/`) et le protocole d'évaluation de non-régression (`arca-test`).

---

### 📄 Fichiers Système du Moteur & Mémoires

- **[[memory]]** : *Mémoire Opérationnelle & Préférences Apprises*
  Buffer d'apprentissage court/moyen terme de l'agent IA, sanctuarisé sous les 50 lignes (style sans tiret cadratin, habitudes techniques, REX projets).
- **[[rules-email]]** : *Règles Métier & Préférences de Tri des Emails*
  Mémoire spécialisée du skill `arca-email-process` consignant les règles d'expéditeurs apprises selon les 3 lots GTD (bruit, références, actions).
- **[[log]]** : *Journal Système Chronologique*
  Consigne chaque action système ou exécutée par l'IA sur une seule ligne horodatée.
- **[[audit-log]]** : *Historique des Audits & Executive Summary ROI*
  Consigne l'évolution temporelle de la santé du Vault, le bilan de productivité des projets et les tendances long terme.
- **[[index]]** : *Index RAG & Cartographie Sémantique Centralisée*
  Indexe l'ensemble des connaissances distillées et des thématiques pour alimenter la recherche sémantique.
