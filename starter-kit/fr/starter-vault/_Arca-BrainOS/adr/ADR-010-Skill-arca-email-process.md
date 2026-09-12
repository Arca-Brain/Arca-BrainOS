---
date: "2026-09-12"
title: "ADR-010 : Architecture et Passerelle du Skill arca-email-process"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-010 : Architecture et Passerelle du Skill arca-email-process

---

## 1. Contexte & Problématique
La gestion quotidienne des emails professionnels et personnels constitue l'une des sources majeures de charge mentale et d'interruption cognitive. Les retours terrain de bêta-testeurs (notamment Baptiste Gandrille, CEO Yuko) ont démontré l'intérêt d'interconnecter le flux de messagerie avec le Second Cerveau Obsidian.

Toutefois, brancher un agent IA sur une boîte de réception soulève des risques architecturaux majeurs :
- **Risque de pollution du coffre :** Importer l'intégralité des corps de texte d'emails sature l'espace, alourdit l'historique Git et dilue la pertinence de la recherche sémantique (RAG).
- **Risque d'intrusion destructive :** Un archivage ou une suppression automatique aveugle par l'IA peut faire disparaître des emails critiques.
- **Risque de dépendance :** Exiger une configuration complexe de libellés Gmail ou un serveur MCP exclusif briserait la portabilité d'Arca-BrainOS.

---

## 2. Décision Retenue
Il est acté de concevoir la compétence `arca-email-process` selon les principes directeurs suivants :

1. **Extraction de Valeur Non Intrusive :** Le rôle exclusif du skill dans le coffre est d'extraire les signaux faibles, les tâches et les synthèses actionnables. Aucun corps de texte d'email brut n'est conservé dans Obsidian.
2. **Ingestion Hybride Résiliente :** Priorité donnée au serveur MCP `google-workspace` (recommandé et documenté), avec bascule gracieuse sur le dossier local `0-Inbox/Emails/` pour les utilisateurs sans MCP. En mode local, les fichiers déposés sont purgés après confirmation explicite.
3. **Routage Direct et Note Récapitulative :**
   - Lorsqu'un projet actif `P-` évident est identifié, l'action simple est injectée directement tout en bas de la liste des tâches du projet, avec traçabilité de l'email source sous la forme : `- [ ] [Action] (Source: [Email de Expéditeur](URL_ou_ID) du Date)`.
   - Lorsqu'aucun projet actif n'est associé, l'ensemble des actions et synthèses orphelines est regroupé dans une note unique `0-Inbox/Triage-Emails-AAAA-MM-JJ.md` dotée d'un frontmatter complet et de liens vers les Domaines de vie (`areas`) et Thèmes (`themes`).
4. **Actions Gmail Natives et Universelles :**
   - Pas de configuration de libellés requise par défaut.
   - Les informations traitées et le bruit sont archivés hors de l'inbox (`removeLabelIds: ["INBOX"]`) et marqués comme lus.
   - Les emails nécessitant une action ou un suivi sont marqués comme lus et reçoivent une étoile (`addLabelIds: ["STARRED"]`), tout en restant visibles dans l'inbox.
   - Support facultatif des libellés personnalisés (`Arca/Traite`, etc.) s'ils existent.
5. **Supervision Humaine Obligatoire :** Déroulement strict en deux temps. Présentation d'un tableau d'alignement dans le chat et attente d'un accord explicite (`ok`) avant toute écriture dans le coffre ou action sur Gmail.
6. **Périmètre et Frugalité :** Requête sur `in:inbox -is:starred` (lus et non lus). Si le volume dépasse 25 emails, traitement automatique du lot de tête des 10 plus récents avec compteur d'emails restants. Commande enrichie acceptant des arguments optionnels (quantité ou filtre Gmail).
7. **Filtre Anti-Boucle & Mémoire Spécialisée Sidecar (`rules-email.md`) :**
   - L'exclusion systématique `-is:starred` empêche de retraiter inutilement les emails d'action maintenus volontairement étoilés dans la boîte de réception.
   - Afin de préserver la frugalité de `memory.md` (sanctuarisé à < 50 lignes selon [[ADR-009-Modele-Memoire-Frugale-CoALA-4-Niveaux]]), les règles de routage spécifiques par expéditeur sont stockées dans une mémoire sidecar dédiée : `_Arca-BrainOS/skills/rules-email.md`, chargée exclusivement lors de l'exécution d'`arca-email-process`.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Allègement direct de la charge mentale liée à la boîte de réception sans risque de perte d'information.
  - Hygiène absolue du coffre préservée (zéro pollution Markdown éphémère).
  - Immédiateté d'usage sans configuration complexe préalable dans Gmail.
  - Traçabilité granulaire de chaque tâche rattachée à son email d'origine.
- **Compromis & Contraintes assumés :**
  - La supervision en deux temps nécessite une présence humaine active lors de l'exécution (choix délibéré de sécurité vs automatisation aveugle).
  - En mode repli local sans MCP, l'utilisateur doit exporter ou copier-coller manuellement ses emails dans `0-Inbox/Emails/`.

---

## 4. Alternatives Écartées
- **Archivage intégral de chaque email en note unitaire :** Rejeté car cela transforme le Second Cerveau en miroir lourd de messagerie et détériore la recherche vectorielle.
- **Inbox Zero automatisé sans supervision :** Rejeté pour des raisons évidentes de sécurité sur les engagements professionnels et personnels.
- **Dépendance stricte à la création de libellés Gmail :** Rejetée car le serveur MCP ne permet pas de créer des libellés à la volée, ce qui aurait imposé une friction d'installation trop lourde.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Retours Bêta : Retours terrain des utilisateurs et bêta-testeurs (Yuko / Airbus)
- Compétence de Crible : [[_Arca-BrainOS/skills/Skill_arca-grill|Skill_arca-grill]]
- Compétence Dérivée : [[_Arca-BrainOS/skills/Skill_arca-email-process|Skill_arca-email-process]]
