# 🛠️ Skill : arca-close-session (Clôture & Mémoire de Session)

- **Processus de Référence :** [[Process-Pilotage-de-Projets-et-Deep-Work]] & [[Process-Capitalisation-et-Synthese-MOC]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-close-session` (ou `close-session` / `brain-close-session`) suivie du nom ou du lien de la note du projet concerné.

## Workflow d'Exécution Séquentiel

1. **Analyse de la Session & Horodatage de Fin :**
   - Parcourt l'historique immédiat de la console et le fichier `_Arca-BrainOS/log.md` du jour pour lister les actions menées sur ce projet (notes distillées, scripts modifiés, bugs identifiés).
   - Ouvre la note du projet cible et repère la session active initiée au sommet de `## 🪵 Journal de Bord des Sessions`.
   - Extrait l'heure d'ouverture `[HH:mm]` consignée lors de `arca-resume` et enregistre l'heure de clôture actuelle `[HH:mm]`.
   - Calcule la durée réelle ($\Delta t_{\text{réel}}$) et évalue de manière autonome (sans solliciter de validation dans le chat) le temps que cela aurait pris sans IA ($T_{\text{sans IA}}$) selon la complexité des tâches réalisées, ainsi que le temps économisé (Gain IA).

2. **Mise à jour de la Liste Principale (Source Unique de Vérité) :**
   - Identifie la section principale des tâches au sommet (généralement `## 🚀 Actions Prochaines Étapes` ou `## Actions todo next`).
   - Coche (`[x]`) chirurgicalement les tâches accomplies durant la session. Si la liste est subdivisée en sous-sections/catégories thématiques (ex: `### [Catégorie]`), localise et coche la tâche à l'intérieur de sa catégorie d'origine.
   - Ajoute les nouvelles tâches identifiées pour la suite sous forme de cases à cocher actives (`- [ ]`) en les classant sous la sous-section/catégorie thématique la plus pertinente.

3. **Finalisation du Bilan Historique dans le Journal :**
   - Remplace le bloc temporaire en attente au sommet de `## 🪵 Journal de Bord des Sessions` par le bilan finalisé structuré selon le template ci-dessous.
   - **Règle absolue** : N'utilise **aucune** case à cocher active (`- [ ]` ou `- [x]`) dans ce journal pour éviter toute désynchronisation. Utilise uniquement des listes à puces textuelles simples (`-`).

4. **Mise à jour des Métadonnées Cumulées du Projet (Frontmatter YAML) :**
   - Lit les métadonnées existantes dans le frontmatter de la note projet (ex: `sessions_count`, `total_real_duration`, `total_estimated_manual`, `total_time_saved`).
   - Incrémente le nombre de sessions (`sessions_count: +1`).
   - Met à jour la date de dernière session (`last_session: "AAAA-MM-JJ"`).
   - Additionne la durée réelle et le temps sans IA aux totaux existants et recalcule le gain cumulé (`total_time_saved`).

5. **Détection d'Habitudes & Capitalisation Frugale (`memory.md`) :**
   - Parcourt les échanges de la session pour détecter si l'utilisateur a formulé une correction explicite, une règle stylistique ou une préférence d'interaction technique forte.
   - Si un arbitrage à fort signal est repéré, formule une proposition dans le message de bilan :
     > *"Durant cette session, tu as arbitré la règle suivante : [Description synthétique]. Souhaites-tu que je l'inscrive dans `_Arca-BrainOS/memory.md` ?"*
   - Ne jamais modifier `memory.md` sans accord explicite de l'utilisateur (zéro écriture furtive).

6. **Journalisation Globale avec Métriques :**
   - Ajoute la ligne de clôture dans `_Arca-BrainOS/log.md` :
     `[AAAA-MM-JJ HH:mm] - Session fermée pour [[Nom-du-Projet]] (Durée: XhYY | Sans IA: ~AhBB | Gain: +ChDD)`

---
## Template de Bilan Historique (à injecter)

### 📅 Session du [AAAA-MM-JJ] : [Titre court de la session]
- **⏱️ Bilan Temporel & Productivité IA :**
  - **Horaires :** [HH:mm début] ➔ [HH:mm fin] (Durée réelle : **XhYY**)
  - **Temps estimé sans IA :** ~AhBB *(Description succincte de la charge)*
  - **Gain de productivité :** 🚀 **+ChDD économisées** (Vitesse **xN.N**)
- **🎯 Objectif atteint lors de cette session :** [Résumé en 1 sentence de ce qui était visé]
- **✅ Tâches accomplies (reportées et cochées en haut) :**
  - [Action 1 accomplie]
  - [Action 2 accomplie]
- **⚠️ Points bloquants & Verrous techniques :**
  - [Ex: Difficultés ou contraintes techniques rencontrées.]
- **🚀 Prochaines étapes (archivées : ajoutées à la liste principale en haut) :**
  - [Priorité 1 pour la réouverture]
  - [Priorité 2]

---
*(Les sessions plus anciennes glissent en dessous)*
