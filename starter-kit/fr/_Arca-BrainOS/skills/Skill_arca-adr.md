# 🛠️ Skill : arca-adr (Scellement de Décision d'Architecture)

- **Processus de Référence :** [[Process-Pilotage-de-Projets-et-Deep-Work]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-adr` (ou `create-adr` / `brain-adr`), suivie du titre ou du thème de la décision d'architecture à consigner. Ce skill est également invoqué en conclusion naturelle d'une session `arca-grill`.

## Objectif
Formaliser, numéroter et figer les arbitrages techniques et conceptuels structurants d'Arca-BrainOS dans le registre dédié `_Arca-BrainOS/adr/` (inspiré des Architectural Decision Records du génie logiciel). L'ADR empêche les régressions futures et évite que l'IA ne remette en question les choix fondateurs du système lors des sessions ultérieures.

## Workflow d'Exécution Séquentiel

### 1. Numérotation, Scan du Registre & Impact
- Scanne le dossier `_Arca-BrainOS/adr/` pour lister les décisions existantes (`ADR-001`, `ADR-002`, etc.) et analyser leurs objets.
- Détermine le prochain numéro séquentiel à 3 chiffres (ex: `001` si le dossier est vide, puis `002`, `011`...).
- **Vérification d'Impact & Remplacement :** Détecte si la nouvelle décision remplace, amende ou rend obsolète un ADR existant. Le cas échéant, prépare la mise à jour du frontmatter de l'ADR antérieur (`status: superseded by [[ADR-XXX]]`).

### 2. Extraction & Rédaction Formelle
- Charge le modèle `_Arca-BrainOS/templates/Template-ADR.md`.
- Rédige la fiche en synthétisant fidèlement les échanges récents (ou la session `arca-grill` préalable) :
  - **Contexte & Problématique :** Raisons de l'arbitrage, frictions initiales et forces en présence.
  - **Décision Retenue :** Choix ferme, formulé au présent et sans ambiguïté.
  - **Conséquences & Compromis :** Bénéfices mesurables et contraintes acceptées.
  - **Alternatives Écartées :** Autres pistes évaluées et motifs d'exclusion.

### 3. Enregistrement & Maillage
- Enregistre la fiche sous le sentier canonique :
  `_Arca-BrainOS/adr/ADR-[Numéro]-[Titre-Normalise].md`
- Ajoute le lien vers la nouvelle décision dans la section `## 🗺️ Working Documents` de [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS.md]] (sous-cluster Moteur Système & Architecture).
- Enregistre la création sur une seule ligne dans `_Arca-BrainOS/log.md` :
  `[AAAA-MM-JJ HH:mm] - Action IA (Architecture) : Création de [[ADR-[Numéro]-[Titre-Normalise]]]`

## Consigne de Sortie
Présente à l'utilisateur la synthèse de la décision scellée et le lien direct vers le fichier créé dans `_Arca-BrainOS/adr/`.
