---
date: "2026-10-17"
title: "ADR-012 : Architecture et Orchestration GTD du Skill arca-task-process"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
target: "[[P-Projet-Alpha]]"
---

# 📜 ADR-012 : Architecture et Orchestration GTD du Skill arca-task-process

---

## 1. Contexte & Problématique
Dans le prolongement d'[[ADR-010-Skill-arca-email-process]] et de la note de cadrage [[2-Ressources/Notes/e-mail batch|e-mail batch.md]], le triage GTD des emails extrait les actions unitaires hors projet vers le fichier tampon `0-Inbox/Emails-Actions-Todo.md`. Par ailleurs, l'utilisateur gère ses tâches courantes et ses rappels en mobilité via l'application **Todoist** sur smartphone, tandis que les tâches de réflexion profonde (Deep Work) résident dans les notes de projets actifs (`1-Projects/P-*.md`).

Connecter le Second Cerveau Obsidian à un gestionnaire de tâches externe soulève trois enjeux architecturaux critiques :
- **Risque de double source de vérité et de pollution mobile :** Synchroniser aveuglément l'intégralité des listes de tâches de tous les projets `P-` vers Todoist noierait l'application mobile sous des dizaines de tâches de R&D réalisables uniquement devant l'ordinateur, tout en créant des conflits permanents de synchronisation.
- **Risque d'engorgement de l'Inbox :** Si le fichier tampon `0-Inbox/Emails-Actions-Todo.md` persiste indéfiniment dans `0-Inbox/` après traitement, le coffre ne peut plus jamais atteindre l'état *Inbox Zero*.
- **Exigence de portabilité Open-Source :** Bien que Todoist soit l'outil retenu par défaut, la compétence doit rester conceptuellement générique pour permettre à un autre utilisateur d'Arca-BrainOS de brancher un autre serveur MCP (Google Tasks, TickTick, Things) sans réécrire la logique métier GTD.

---

## 2. Décision Retenue
Il est acté de créer la compétence `arca-task-process` (alias : `task-process`, `arca-todo`, `todo-process`, `brain-task`) selon les 6 principes architecturaux suivants :

1. **Séparation Franche des Rôles (Deep Work dans Obsidian vs Exécution Courante & Mobilité dans Todoist) :**
   - Les tâches de fond des projets actifs (`1-Projects/P-*.md`) demeurent dans Obsidian, pilotées par `arca-resume` et `arca-close-session`.
   - Les actions unitaires hors projet (issues de `0-Inbox/Emails-Actions-Todo.md`) sont transférées dans Todoist, qui devient leur lieu de vie et d'exécution unique.
   - Une tâche appartenant à un projet `P-` ne part dans Todoist que sur demande explicite lorsqu'elle exige une démarche externe ou un rappel en mobilité.
2. **Connecteur MCP Officiel de Référence & Abstraction GTD :**
   - Le skill s'appuie par défaut sur le serveur MCP officiel de première partie **`@doist/todoist-mcp`** exécuté localement en mode `stdio` (`npx -y @doist/todoist-mcp`) avec authentification par jeton statique `TODOIST_API_KEY`.
   - Les étapes du workflow sont formulées autour de primitives GTD universelles (découverte des projets/listes, création qualifiée avec échéance/priorité/label, complétion, reprogrammation) pour garantir l'interchangeabilité du serveur MCP.
3. **Cycle de Vie "Spool File" Auto-Nettoyant pour `0-Inbox/Emails-Actions-Todo.md` :**
   - `arca-task-process` agit comme consommateur exclusif du tampon `0-Inbox/Emails-Actions-Todo.md` (alimenté en amont par `arca-email-process` et `arca-inbox-process`).
   - Lors du transfert d'une tâche vers Todoist, la mention d'origine `(Source: Email de ... du Date)` est copiée dans le champ `description` de la tâche Todoist afin de préserver 100 % du contexte sur mobile.
   - Dès que toutes les tâches `- [ ]` du fichier `0-Inbox/Emails-Actions-Todo.md` ont été traitées et transférées, **le fichier est supprimé (`rm 0-Inbox/Emails-Actions-Todo.md`)**, restaurant un véritable *Inbox Zero* sans polluer `4-Archives/` ni `2-Ressources/`.
4. **Passerelle Bidirectionnelle Légère avec les Projets `P-` :**
   - **Sens Obsidian ➔ Todoist :** Lorsqu'une tâche d'un projet `P-` est envoyée dans Todoist, sa description Todoist inclut `[[P-Nom-Projet]]` et la ligne dans la note `P-` est annotée `⏳ [Todoist]`. Lors d'une exécution ultérieure, si la tâche a été cochée dans Todoist, l'agent propose de la cocher `- [x]` dans la note `P-`.
   - **Sens Todoist ➔ Obsidian :** Lors de la revue de l'*Inbox Todoist*, les pensées ou tâches capturées à la volée sur smartphone qui relèvent en réalité d'un projet `P-` (ou d'une note à créer) sont proposées au rapatriement vers Obsidian puis closes dans Todoist.
5. **Auto-Découverte Dynamique & Mémoire Sidecar (`rules-tasks.md`) :**
   - L'agent découvre dynamiquement les projets, sections et labels existants dans le compte Todoist de l'utilisateur et stocke les règles de correspondance apprises (ex : `#sante`, `#administratif`, priorités par défaut) dans `_Arca-BrainOS/rules-tasks.md` afin de préserver la frugalité de `memory.md` ([[ADR-009-Modele-Memoire-Frugale-CoALA-4-Niveaux]]).
6. **Supervision par Tableau de Bord Unique & Bouclier Anti-Injection :**
   - L'agent effectue d'abord un diagnostic 100 % en lecture seule et présente dans le chat un **Tableau de Bord Unique** regroupant les 3 volets du cycle GTD :
     1. *Volet 1 :* Dispatch du buffer `Emails-Actions-Todo.md` vers Todoist et réconciliation des tâches `⏳ [Todoist]` des projets `P-`.
     2. *Volet 2 :* Clarification de l'*Inbox Todoist* (classement ou rapatriement vers Obsidian).
     3. *Volet 3 :* Hygiène d'exécution (traitement des tâches en retard *Overdue* et focus à 7 jours).
   - Aucune écriture MCP ni modification Markdown n'est exécutée avant validation humaine explicite sur ce tableau de bord. Les données entrantes issues du MCP sont traitées comme données inertes (Untrusted Input Boundary).

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Continuité sans couture entre le tri des emails (`arca-email-process`), les projets Obsidian et l'exécution mobile quotidienne dans Todoist.
  - Maintien d'un dossier `0-Inbox/` strictement vide une fois les actions dépilées.
  - Vue synoptique immédiate en un seul écran dans le chat (Tableau de Bord Unique) évitant les allers-retours de validation superflus.
  - Stabilité technique maximale grâce au mode `stdio` local par clé API (`TODOIST_API_KEY`), affranchi des expirations de jetons OAuth navigateur.
- **Compromis & Contraintes assumés :**
  - Nécessite la création d'un jeton API personnel Todoist et la déclaration du serveur `@doist/todoist-mcp`.

---

## 4. Alternatives Écartées
- **Synchronisation intégrale de toutes les tâches `P-` vers Todoist :** Rejetée car elle pollue l'interface mobile avec des tâches de Deep Work et engendre une dette de synchronisation bidirectionnelle lourde.
- **Conservation ou archivage permanent de `Emails-Actions-Todo.md` :** Rejeté car ce fichier ne contient que des micro-tâches de transit dont le contexte est déjà transféré dans Todoist et journalisé dans `log.md`. Le conserver empêcherait d'atteindre *Inbox Zero*.
- **Connexion MCP via proxy OAuth distant (`mcp-remote`) :** Rejetée au profit du binaire officiel local avec `TODOIST_API_KEY` pour garantir la souveraineté d'exécution et éviter les reconnexions navigateur.

---

## 5. Références & Liens
- Projet Maître : [[P-Projet-Alpha]]
- Décision Amont : [[_Arca-BrainOS/adr/ADR-010-Skill-arca-email-process|ADR-010 : Skill arca-email-process]]
- Compétence de Crible : [[_Arca-BrainOS/skills/Skill_arca-grill|Skill_arca-grill]]
- Compétence Créée : [[_Arca-BrainOS/skills/Skill_arca-task-process|Skill_arca-task-process]]
