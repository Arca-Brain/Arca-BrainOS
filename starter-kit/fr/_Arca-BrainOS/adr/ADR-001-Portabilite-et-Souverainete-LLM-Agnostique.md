---
date: "2026-08-09"
title: "ADR-001 : Portabilité et Souveraineté LLM-Agnostique (Du Cloud Souverain au 100% Local)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-001 : Portabilité et Souveraineté LLM-Agnostique (Du Cloud Souverain au 100% Local)

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
La plupart des outils d'IA pour la gestion des connaissances personnelles (PKM) et la prise de notes enferment l'utilisateur dans une dépendance technologique et économique critique (Vendor Lock-in). Ils s'adossent à des APIs propriétaires fermées (OpenAI, Anthropic) ou à des serveurs cloud centralisés sans garantie de confidentialité (Zero Data Retention).

Cette situation présente des risques majeurs :
- **Perte de souveraineté :** L'utilisateur confie ses réflexions les plus intimes et stratégiques à des tiers soumis au Cloud Act.
- **Obsolescence programmée :** Dès qu'un fournisseur d'API déprécie un modèle, augmente ses tarifs ou modifie ses conditions générales, le Second Cerveau cesse de fonctionner.
- **Incompatibilité professionnelle :** Les environnements en entreprise (Airbus, santé, finance, juridique) interdisent formellement l'envoi de données internes vers des clouds publics non souverains.

---

## 2. Décision Retenue
Il est acté de concevoir l'intégralité d'Arca-BrainOS de manière **100 % LLM-agnostique et indépendante de l'infrastructure d'exécution** :

1. **Prompts & Compétences en Markdown Universel :** Toutes les compétences (`Skill_arca-*.md`), les fiches de processus (`Process-*.md`) et la constitution (`AGENTS.md`) sont rédigées en texte brut Markdown déterministe, sans dépendance vis-à-vis d'un framework d'agents propriétaire (LangChain, AutoGen, CrewAI).
2. **Découplage Absolu Moteur vs Runner :** Le moteur réside dans le coffre local. L'utilisateur est libre d'exécuter Arca-BrainOS sur l'infrastructure de son choix selon ses impératifs de budget, de puissance et de sécurité :
   - *Runners Cloud de pointe :* Google Antigravity CLI (Gemini Pro), Claude Code (Claude 3.5 Sonnet), OpenAI Codex.
   - *Hébergeurs Cloud Souverains & RGPD :* Scaleway, Mistral AI, OVHcloud.
   - *Runners 100 % Locaux & Air-Gapped (ZDR absolu) :* Ollama, LM Studio, vLLM, llama.cpp (Qwen 2.5, DeepSeek, Llama 3).
3. **Pérennité du Format :** Même en cas de coupure réseau complète ou de disparition des géants du cloud, le coffre reste lisible, éditable et opérationnel en local.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Souveraineté totale et pérennité décennale garantie des données personnelles.
  - Portabilité immédiate : le même coffre peut être piloté par Antigravity le matin et par Ollama en local déconnecté le soir.
  - Déploiement possible dans des contextes professionnels ultra-sécurisés sans enfreindre les politiques de sécurité informatique.
- **Compromis & Contraintes assumés :**
  - Refus délibéré d'utiliser les fonctions de "function-calling" propriétaires exclusives à un seul fournisseur de LLM, au profit de protocoles universels (fichiers Markdown, CLI POSIX, MCP standard).

---

## 4. Alternatives Écartées
- **Plugin Obsidian dédié en TypeScript :** Rejeté car il enfermerait le workflow dans Obsidian et empêcherait son exécution en ligne de commande ou dans d'autres éditeurs (VS Code, terminal natif).
- **Framework d'orchestration Python externe (CrewAI, LangChain) :** Rejeté car il introduirait une lourde dette technique de dépendances Python, des risques de rupture d'API et une friction d'installation incompatible avec la simplicité du Markdown.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Manifeste Fondateur : [[MANIFESTO.fr.md|Manifeste du Workflow Augmenté]]
- Note de Veille : [[2-Ressources/Notes/Veille-Synthetic-LLM-Prive-ZDR|Veille LLM Privé ZDR]]
- Guide d'Installation : [[INSTALL.fr.md|Guide d'Installation Multi-Runners]]
