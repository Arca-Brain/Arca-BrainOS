# 🛠️ Skill : arca-grill (Crible Socratique & Revue Contradictoire de Compétences)

- **Processus de Référence :** [[Process-Pilotage-de-Projets-et-Deep-Work]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-grill` (ou `grill-me` / `brain-grill`), suivie du nom, de l'idée ou du besoin d'un nouveau skill (ou de la modification d'un skill existant) pour Arca-BrainOS.

## Objectif
Agir comme un sparring-partner et un contradicteur d'ingénierie rigoureux (adapté de la méthode *Grilling* de Matt Pocock). L'IA suspend immédiatement toute écriture de prompt ou de code pour soumettre l'idée à un crible socratique systématique, afin d'éliminer le flou conceptuel ("vibe coding"), d'éviter l'inflation de compétences inutiles et de garantir la robustesse architecturale d'Arca-BrainOS.

## Périmètre (Phase 1)
Ce skill est strictement focalisé sur **la conception, la refonte et l'évolution des compétences agentiques (`Skill_arca-*.md`) d'Arca-BrainOS**. L'extension aux projets génériques du coffre est réservée à une phase ultérieure.

## Les 3 Piliers Méthodologiques (Pocock)

1. **L'Arbre de Conception (Design Tree) :** Le problème est modélisé mentalement comme un arbre de décisions, où chaque choix fondamental conditionne des sous-choix.
2. **La Frontière (Frontier) :** La frontière regroupe l'ensemble des décisions dont les prérequis sont déjà tranchés. Ce sont les seules questions légitimes à poser *maintenant*, sans présumer des réponses futures. Deux questions ne partagent jamais un même round si l'une dépend de l'autre.
3. **Les Rounds :** Le questionnement progresse par rounds successifs. Si 2 à 3 rounds suffisent habituellement à trancher les fondations architecturales, des rounds additionnels (Round 4, 5...) sont vivement encouragés dès que des arbitrages fins d'ergonomie ou des cas limites subsistent. La session ne s'arrête pas à un quota fixe, mais uniquement lorsque toute la frontière est épuisée.

## Séparation Faits vs Décisions
- **Les Faits relèvent de l'IA :** Quand une question nécessite d'examiner le coffre (skills existants, dossiers, configurations, serveurs MCP disponibles), l'IA inspecte elle-même l'environnement au lieu d'interroger l'utilisateur.
- **Les Décisions relèvent exclusivement de l'Humain :** L'IA formule une recommandation claire et argumentée pour chaque question, mais ne tranche jamais une décision à la place de l'utilisateur.

## Grille d'Analyse pour Explorer la Frontière
Pour alimenter les questions de chaque round, l'IA sonde systématiquement ces 5 axes critiques :
1. **Légitimité & Frugalité :** Nouveau skill distinct vs extension d'une compétence existante ? Quel est le gain concret vs la complexité ajoutée ?
2. **Vecteurs d'Ingestion & Dépendances :** Formats d'entrée (fichiers Markdown, flux stdin, serveurs MCP, transcripts) ? Dépendances ou outils requis ?
3. **Gouvernance & Sécurité du Vault :** Zones d'écriture, sanctuarisation des notes humaines, respect des garde-fous (règle des 3 fichiers max).
4. **Autonomie vs Supervision Humaine :** Étapes en automatique pur (anti-chatter) vs points de contrôle obligatoires dans le chat.
5. **Contrat de Sortie & Robustesse :** Modèle YAML attendu, structure du fichier produit, gestion des cas d'erreur ou d'absence de données.

## Workflow d'Exécution Séquentiel

### 1. Analyse Initiale & Scan des Invariants (ADR)
- Analyse le besoin ou l'intention exprimée par l'utilisateur.
- **Scan du Registre Architectural :** Inspecte systématiquement le dossier `_Arca-BrainOS/adr/` (notamment `adr/README.md` et les ADRs actifs) pour identifier les contraintes, compromis et invariants déjà tranchés (ex: souveraineté LLM-agnostique ADR-001, architecture découplée ADR-002, sanctuarisation de la zone humaine ADR-005, mémoire frugale CoALA ADR-009). Si la proposition entre en tension avec un ADR existant, cette tension devient immédiatement une question prioritaire de frontière dès le Round 1.
- Vérifie les faits dans l'environnement (fichiers existants, topographie, configurations, serveurs MCP disponibles).
- **Règle absolue :** N'écrire aucun fichier `.md`, ne modifier aucun index à ce stade. L'IA reste en posture d'interview synchrone dans le chat.

### 2. Déroulement par Rounds sur la Frontière
Pour chaque round de questions :
- Identifier les décisions prêtes à être arbitrées (la frontière active).
- Ne jamais inclure deux questions interdépendantes dans le même round.
- Présenter le round dans le **format standardisé strict** suivant :

```markdown
❓ **Q1** - **<Titre de la décision>** : <Corps détaillé de la question, contexte, enjeux et options envisageables>

➡️ <Recommandation argumentée de l'IA avec justification pragmatique>

---

❓ **Q2** - **<Titre de la décision>** : <Corps détaillé de la question...>

➡️ <Recommandation argumentée de l'IA>

---
```

Ce format permet à l'utilisateur de répondre vite par numéro (ex : `1: ok rec`, `2: option B`, `3: non car...`).

### 3. Évolution de la Frontière & Rounds Additionnels
- Dès réception des réponses, acter les arbitrages.
- Débloquer les branches avales de l'arbre de conception : la frontière avance.
- Si de nouvelles décisions dépendantes, des cas limites (edge cases) ou des choix de micro-ergonomie subsistent, enchaîner sans hésiter sur le Round suivant (Round 4, Round 5...).
- Ne jamais forcer la clôture prématurée : réitérer jusqu'à ce que la frontière soit véritablement vide (zéro zone d'ombre technique ou ergonomique).

### 4. Synthèse d'Alignement & Passage de Relais
Lorsque la frontière est vide :
- Rédiger une **Synthèse de Cadrage Partagé** récapitulant les décisions actées, les options rejetées, les contraintes d'implémentation et le modèle d'interaction retenu.
- Proposer l'enchaînement opérationnel :
  1. Rédiger et sceller la décision d'architecture via `arca-adr` dans `_Arca-BrainOS/adr/`.
  2. Implémenter le skill dans `_Arca-BrainOS/skills/Skill_arca-[nom].md`.
  3. Mettre à jour `_Arca-BrainOS/skills/README.md` et `AGENTS.md`.

## Consignes de Style & Sécurité
- Ton direct, incisif, professionnel et constructif.
- **Bannissement absolu du tiret cadratin :** Remplacer systématiquement par des deux-points, des virgules, des points ou des parenthèses.
- **Zéro effet de bord prématuré :** Aucun fichier ne doit être créé ou modifié dans le coffre avant la validation explicite de la synthèse d'alignement.
