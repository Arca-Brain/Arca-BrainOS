# 🛠️ Skill : arca-email-process (Triage GTD des Emails & Extraction d'Actions)

- **Processus de Référence :** [[Process-Inbox-Clean-et-Dispatch]]
- **Décision d'Architecture de Référence :** [[ADR-010-Skill-arca-email-process]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-email-process` (ou `email-process` / `brain-email`), éventuellement suivie d'un nombre limite ou d'une requête spécifique (ex : `arca-email-process 5`, `arca-email-process "from:direction"`).

## Objectif
Analyser le flux des emails de la boîte de réception, en extraire de manière chirurgicale les tâches, relances et synthèses pour les ancrer dans le Second Cerveau Obsidian sans jamais conserver de corps bruts d'emails, puis appliquer un archivage ou un étiquetage Gmail supervisé et réversible.

## Prérequis & Vecteur d'Ingestion Hybride
1. **Vecteur Préférentiel (Recommandé) :** Serveur MCP `google-workspace` actif (`search_emails`, `get_email`, `modify_email_labels`).
2. **Vecteur de Repli (Local) :** Si le MCP n'est pas configuré, le skill scanne le dossier local `0-Inbox/Emails/` pour y traiter les fichiers `.eml` ou `.md` déposés manuellement.

## Workflow d'Exécution Séquentiel

### 1. Récupération du Flux, Frugalité & Mémoire Métier
- **Mémoire Spécialisée Sidecar :** Charge systématiquement le fichier de règles `_Arca-BrainOS/skills/rules-email.md` pour appliquer les préférences d'expéditeurs déjà apprises.
- **Requête par défaut (Filtre anti-doublon) :** Cible `in:inbox -is:starred` (messages lus ou non lus, mais **exclut formellement les emails déjà étoilés** pour ne jamais retraiter les tâches en cours).
- **Garde-fou volumétrique :** 
  - Si l'Inbox contient plus de 25 emails non traités, le skill restreint l'analyse au **lot de tête des 10 plus récents**.
  - Affiche en introduction le compteur d'encours : *"XX emails non traités au total dans la boîte de réception. Traitement du lot de tête (10 récents) en cours..."*
- **Surcharge utilisateur :** Si un argument est passé dans la commande (ex : `20` ou `"from:baptiste"`), applique directement cette restriction.

### 2. Analyse & Grille de Qualification GTD
Pour chaque email du lot, l'IA consulte `rules-email.md` en priorité, puis qualifie le message selon 4 catégories :
1. **⚡ Action Projet :** Tâche claire et directe rattachable à un projet actif existant `P-`.
2. **⏳ En Attente / Relance :** Suivi d'une délégation, attente d'une validation ou d'un retour d'un tiers.
3. **📚 Information & Veille :** Donnée utile, contact ou synthèse sans action immédiate, rattachable à un Domaine de vie (`3-Domaines-de-vie/`) ou un Thème (`T-`).
4. **🗑️ Bruit / Archive :** Notification, accusé de réception, newsletter ou échange clos sans valeur cognitive résiduelle.

### 3. Supervision Humaine Obligatoire (Point d'Arrêt)
L'IA suspend immédiatement toute écriture dans le coffre ou action sur Gmail. Elle affiche dans le chat le tableau d'alignement complet :

```markdown
| # | Expéditeur | Objet | Catégorie GTD | Action / Synthèse extraite | Destination Vault | Action Gmail Prévue |
|---|------------|-------|---------------|----------------------------|-------------------|---------------------|
| 1 | Nom        | Sujet | Action Projet | Rédiger le compte-rendu    | [[P-Projet-X]]    | Étoile + Lu         |
| 2 | Nom        | Sujet | Bruit         | Aucune                     | Néant (ignoré)    | Archiver + Lu       |
```

- **Règle absolue :** L'IA attend la confirmation explicite de l'utilisateur (`ok` ou ajustements sur certains numéros) avant de passer à l'étape suivante.

### 4. Exécution & Routage dans le Coffre
Une fois le feu vert reçu :

- **Cas A : Actions avec Projet Actif identifié (`P-`) :**
  - Ouvre la note du projet `1-Projects/[P-Nom].md`.
  - Injecte l'action tout en bas de la liste des tâches générales sous `## 🎯 Objectifs & Tâches` :
    `- [ ] <Description de l'action> (Source: [Email de Expéditeur](Lien_ou_ID) du Date)`
  - *Règle de respect humain :* Ne jamais modifier ni supprimer les tâches préexistantes de l'utilisateur.

- **Cas B : Actions Orphelines, Relances ou Synthèses (Sans Projet Actif) :**
  - Si des actions orphelines ou des synthèses subsistent, crée une note unique dans `0-Inbox/Triage-Emails-AAAA-MM-JJ.md`.
  - Utilise le modèle standard suivant :
    ```yaml
    ---
    date: AAAA-MM-JJ
    title: "Triage Emails : AAAA-MM-JJ"
    category: note
    tags:
      - email
      - triage
      - inbox-zero
    areas:
      - "[[Travail]]"
    themes: []
    ---
    ```
  - Structure le contenu avec les sections :
    - `## 🎯 Actions Immédiates (Sans Projet)`
    - `## ⏳ En Attente & Relances Déléguées`
    - `## 📚 Informations & Contacts Notables`

### 5. Actions Messagerie Gmail & Nettoyage
- **Via MCP `google-workspace` :**
  - Pour les emails Bruit / Informations traitées : `removeLabelIds: ["INBOX"]` (Archivage) et `removeLabelIds: ["UNREAD"]` (Marqué lu).
  - Pour les emails Action / En attente : `removeLabelIds: ["UNREAD"]` (Marqué lu) et `addLabelIds: ["STARRED"]` (Étoile de suivi), en les maintenant visibles dans l'Inbox.
  - Si des libellés personnalisés ont été configurés par l'utilisateur (ex : `Arca/Traite`), ils sont appliqués en complément.
- **En Mode Repli Local :**
  - Supprime les fichiers traités du dossier `0-Inbox/Emails/` après accord, conformément à la décision de ne conserver aucun corps brut dans le coffre.

### 6. Clôture & Journalisation
Enregistre l'opération sur une seule ligne dans `_Arca-BrainOS/log.md` :
`[AAAA-MM-JJ HH:mm] - Action IA (Email) : Triage de [N] emails ([X] actions injectées dans les projets, [Y] archivés)`

## Consignes de Style & Sécurité
- Zéro tiret cadratin dans tous les fichiers générés ou édités : utiliser exclusivement des deux-points, des virgules ou des parenthèses.
- Zéro action destructrice ou modification de labels sans validation préalable dans le chat.
