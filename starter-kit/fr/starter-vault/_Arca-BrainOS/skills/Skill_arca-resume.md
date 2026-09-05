# 🛠️ Skill : arca-resume (Relance & Cadrage de Session Deep Work)

- **Processus de Référence :** [[Process-Pilotage-de-Projets-et-Deep-Work]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-resume` (ou `resume` / `brain-resume`) suivie du nom ou du lien de la note du projet concerné.

## Objectif
Ré-immerger l'utilisateur dans son contexte de travail avant de démarrer une session. Ce skill agit comme un partenaire de réflexion stratégique pour clarifier l'intention du run actuel, en faisant le lien entre les 2-3 dernières sessions et le prochain jalon de livrables, sans modifier ou cocher de tâches dans la note de projet.

## Workflow d'Exécution Séquentiel

1. **Chargement & Analyse du Contexte :**
   - Charge en mémoire la note du projet cible (ex: `[[P-[Nom-Projet]]]]`) **ainsi que l'ensemble des notes de travail liées dans sa section `## 🗺️ Working Documents` (ou équivalente)** pour appréhender le contexte exact des chantiers en cours.
   - Analyse la section `## 🪵 Journal de Bord des Sessions` en lisant les **2 ou 3 dernières entrées** pour comprendre la dynamique récente (les réalisations et les verrous restants).
   - Analyse la section `## 📌 Livrables & Jalons (Milestones)` pour identifier la phase active en cours et le prochain jalon à livrer.

2. **Élaboration du Diagnostic de Relance :**
   - Rédige un briefing axé sur l'alignement et la clarté, structuré ainsi :
     - **📋 État des lieux (Dernières sessions) :** Synthèse rapide de la dynamique des 2-3 derniers runs (ce qui a été fait, les points de blocage persistants).
     - **🎯 Prochain Livrable Visé :** Rappel du jalon actif en cours (dans la section Milestones) et ce qu'il reste à accomplir pour le finaliser.
     - **💡 Intention de Session proposée (Focus principal) :** Une suggestion claire de 2 ou 3 actions ciblées à mener *durant cette session précise* pour débloquer ou faire avancer ce jalon.
     - **🛠️ Autres actions possibles (Optionnelles) :** Une liste secondaire des autres tâches ou pistes en attente pour ce jalon ou le projet, pour conserver une vision d'ensemble.

3. **Phase Interactive (Clarification de l'Intention) :**
   - Présente ce briefing à l'utilisateur dans le chat.
   - Demande à l'utilisateur de clarifier ou d'ajuster l'objectif du run : *"Es-tu d'accord avec cette intention pour aujourd'hui, ou souhaites-tu réorienter le focus de notre session de travail ?"*
   - **Règle absolue** : Le but ici est uniquement de cadrer mentalement la session de travail et d'aligner l'IA sur l'intention humaine. Aucun changement de cases à cocher ou de réorganisation n'est effectué dans la note projet par ce skill.

4. **Initiation du Journal & Horodatage :**
   - Une fois l'intention de session validée par l'utilisateur, l'IA se met en posture de travail prête à l'exécuter.
   - Repère la section `## 🪵 Journal de Bord des Sessions` dans la note de projet (en la créant en bas de note si elle n'existe pas).
   - Injecte au sommet de cette section (ordre antichronologique) le bloc initial de session :
     ```markdown
     ### 📅 Session du [AAAA-MM-JJ]
     - **⏱️ Horaires :** [HH:mm] ➔ *[Session en cours...]*
     - ⏳ *Session active : en attente de clôture par `arca-close-session`*

     ---
     ```
   - Ajoute la ligne d'ouverture avec horodatage dans `/_Arca-BrainOS/log.md` :
     `[AAAA-MM-JJ HH:mm] - Session relancée pour [[Nom-du-Projet]]`
