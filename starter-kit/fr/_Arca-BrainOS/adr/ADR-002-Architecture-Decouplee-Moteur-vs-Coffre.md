---
date: "2026-08-09"
title: "ADR-002 : Architecture Découplée en 2 Parties (Moteur _Arca-BrainOS/ vs Coffre)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-002 : Architecture Découplée en 2 Parties (Moteur _Arca-BrainOS/ vs Coffre)

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
Intégrer une couche d'intelligence artificielle et d'automatisation agentique au sein d'un coffre personnel Obsidian pose un dilemme d'architecture fondamental :
- Si l'outillage agentique est dispersé parmi les notes de l'utilisateur, le coffre devient confus, les fichiers système polluent la navigation quotidienne et les mises à jour du moteur risquent d'écraser des notes personnelles.
- Si l'outillage est enfoui dans le dossier interne `.obsidian/`, il devient invisible, difficilement versionnable sous Git et inaccessible aux agents CLI exécutés hors de l'application Obsidian.

---

## 2. Décision Retenue
Il est acté d'adopter une **architecture découplée en 2 parties étanches** :

1. **Le Moteur Agentique Autonome (`_Arca-BrainOS/`) :**
   - L'ensemble de la mécanique logicielle réside dans un dossier unique préfixé d'un tiret bas : `_Arca-BrainOS/`.
   - Ce dossier regroupe les compétences (`skills/`), les processus (`process/`), les modèles (`templates/`), les décisions (`adr/`), le journal d'audit (`log.md`) et la mémoire de travail (`memory.md`).
   - Ce composant est 100 % portable : il peut être copié, mis à jour par Git ou retiré sans altérer les notes de l'utilisateur.
2. **Le Coffre Souverain de l'Utilisateur :**
   - Toutes les connaissances, projets et réflexions résident dans l'arborescence standard visible de l'utilisateur (`0-Inbox/`, `1-Projects/`, `2-Ressources/`, `3-Domaines-de-vie/`, `4-Archives/`).
3. **Le Pont Constitutionnel Universel (`AGENTS.md`) :**
   - Un unique fichier racine `AGENTS.md` agit comme la boussole universelle et le prompt système de référence, traduisant les variables de chemins (`PATH_*`) pour n'importe quel modèle d'IA.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Modularité absolue : mise à jour du moteur par simple synchronisation de `_Arca-BrainOS/` sans risque pour les données personnelles.
  - Compatibilité native avec n'importe quel éditeur de texte brut (Obsidian, VS Code, Logseq, Neovim).
  - Lisibilité immédiate : l'utilisateur sait exactement où se trouve la machinerie de l'IA et où résident ses propres écrits.
- **Compromis & Contraintes assumés :**
  - Nécessite de maintenir rigoureusement la déclaration des chemins canoniques dans `AGENTS.md`.

---

## 4. Alternatives Écartées
- **Enfouissement dans `.obsidian/plugins/` :** Rejeté car cela exclut l'usage en ligne de commande via CLI et lie le projet aux APIs internes d'Obsidian.
- **Dissémination des prompts dans les dossiers thématiques :** Rejetée car elle crée une confusion permanente entre matière cognitive et code d'orchestration.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Constitution du Coffre : [[AGENTS.md]]
- Documentation d'Architecture : [[README.md|README Officiel Arca-BrainOS]]
