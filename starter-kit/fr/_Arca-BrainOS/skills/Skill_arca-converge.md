# 🛠️ Skill : arca-converge (Fusion MOC & Convergence)

- **Processus de Référence :** [[Process-Ingestion-et-Distillation-de-Medias]] & [[Process-Capitalisation-et-Synthese-MOC]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-converge` (ou `brain-converge`, généralement suivie d'une note distillée ou d'une liste de notes).

## Objectif
Ancrer les nouvelles notes de synthèse dans la structure globale du Second Cerveau en mettant à jour les Cartes de Contenu (MOC / Thèmes) et en assurant le maillage directionnel, sans aucune étape de validation ou de relecture.

## Workflow d'Exécution Séquentiel

1. **Identification des Thèmes (MOC) :**
   - Analyse la note source (ex: `AI-Distil-...`) et identifie le ou les thèmes/MOCs associés (fichiers commençant par `T-` situés dans `2-Ressources/Themes/` ou ses sous-dossiers thématiques, ou le dossier `1-Projects/`).
   - Si le fichier `T-[Thème].md` correspondant n'existe pas, crée-le automatiquement.

2. **Mise à jour du MOC (Ancrage descendant) :**
   - Ouvre le fichier `T-[Thème].md` identifié.
   - Ajoute un lien vers la nouvelle note distillée sous la section appropriée (ex: `## Ressources & Synthèses`).
   - Rédige une micro-description d'une ligne maximum à côté du lien pour donner du contexte.

3. **Maillage de la Note (Ancrage ascendant) :**
   - Retourne sur la note distillée source originale.
   - Dans la section `## Connexions Suggérées`, transforme les suggestions textuelles en véritables liens Obsidian fonctionnels `[[T-[Thème]]]` vers les MOCs mis à jour.

4. **Indexation & Journalisation (Automatique) :**
   - Ajoute la nouvelle note à l'index central `_Arca-BrainOS/index.md` sous la section correspondant au MOC principal. Si aucune section existante ne correspond, crée une nouvelle section cohérente ou choisis la plus proche.
   - Enregistre l'action sur une seule ligne dans `_Arca-BrainOS/log.md` avec le format strict :
     `[Date] - Convergence OK : [[AI-Distil-...]] ancré dans [[T-[Thème]]]`

## Règles d'Écriture et Limitations
- **Gestion des 3 fichiers (Garde-fous de sécurité) :** Si les modifications cumulées (MOCs, log, index, projets) dépassent la limite de 3 fichiers créés ou modifiés hors de `2-Ressources/IA-generated/` au cours d'un même workflow, présente le plan de modification de manière claire dans le chat et demande une confirmation explicite à l'utilisateur avant de procéder à l'écriture des fichiers restants.
- **Aucun Statut :** Ne pas injecter de tag ou de métadonnée `#to-review` ou `status:`. Les notes sont considérées comme revues et classées par défaut.
- **Rangement MOC :** Ne pas toucher aux structures de listes complexes créées par l'utilisateur dans les MOCs, ajouter les nouveaux liens uniquement en fin de section dédiée.
- **Sécurité & Liage des Projets :** La mise à jour des thèmes `T-[Thème].md` situés dans `1-Projects/` ou `2-Ressources/Themes/` est pleinement autorisée pour y insérer les liens de convergence. De plus, conformément aux règles globales, tu as l'autorisation d'ajouter des liens Obsidian `[[...]]` et de mettre à jour les listes de tâches (`- [ ]`) dans les notes de projet (`P-`) et de leçons (`L-`) situées dans `1-Projects/` afin de renforcer le maillage thématique, tout en préservant le contenu rédigé par l'utilisateur. Ne jamais tenter d'écrire ou modifier des fichiers dans `3-Areas/`.
