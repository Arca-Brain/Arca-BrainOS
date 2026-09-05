# 🛠️ Skill : arca-distill (Le Master Skill d'Orchestration)

- **Processus de Référence :** [[Process-Ingestion-et-Distillation-de-Medias]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-distill` (ou `distill` / `brain-distill` / `brain-distil`) suivie du nom ou du lien d'un fichier situé dans `0-Inbox/` (ou un de ses sous-dossiers, comme `0-Inbox/Youtube/`).

## Workflow d'Exécution Séquentiel
1. **Étape 1 : Synthèse & Distillation**
   - Charge en mémoire le fichier source brut.
   - Invoque et exécute le workflow complet de `Skill_arca-synthesize.md` pour générer la note de synthèse structurée `AI-Distil-[Nom].md` dans `2-Ressources/IA-generated/`.

2. **Étape 2 : Convergence & Maillage automatique**
   - Applique immédiatement le workflow de `Skill_arca-converge.md` sur la note fraîchement générée.
   
3. **Étape 3 : Archivage physique et Nettoyage de l'Inbox**
   - Une fois la synthèse et le maillage terminés, déplace le fichier source brut d'origine (situé dans `0-Inbox/` ou un de ses sous-dossiers) vers sa destination définitive sous `2-Ressources/Notes/`.
   - Utilise une commande shell de déplacement direct (`mv` via `run_command`) pour effectuer cette opération de manière propre et définitive.

4. **Étape 4 : Analyse d'Impact & Alignement (Interactif)**
   - Invoque le workflow de `Skill_arca-impact.md` sur la note générée pour proposer les recommandations d'intégration dans vos projets et thèmes.

## Consigne de Sortie
Ce skill s'exécute de manière totalement transparente et enchaîne les étapes. Une fois le processus terminé, affiche simplement un récapitulatif succinct dans le chat : "Enchaînement terminé : Fichier synthétisé et maillé dans le Vault."
