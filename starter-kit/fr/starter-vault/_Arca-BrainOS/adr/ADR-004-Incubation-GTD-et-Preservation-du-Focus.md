---
date: "2026-08-09"
title: "ADR-004 : Incubation GTD (1-Projects/_Incubation/) et Préservation du Focus Chaud"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-004 : Incubation GTD (1-Projects/_Incubation/) et Préservation du Focus Chaud

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
Dans la méthodologie PARA classique, un projet est binaire : soit il est en cours dans `Projects/`, soit il est terminé dans `Archives/`.
Ce modèle crée un angle mort critique identifié par la méthode GTD (*Getting Things Done* de David Allen) : que faire des chantiers potentiels, des projets exploratoires ou des intentions futures (*Someday / Maybe*) ?
- Si ces projets sont créés directement dans `1-Projects/`, ils submergent le cockpit quotidien (`Home.md`), diluent le focus mental et génèrent un sentiment d'accablement.
- S'ils restent de simples puces dans une note de liste ou sont relégués dans les ressources, ils perdent leur statut de projet et ne sont jamais approfondis.

---

## 2. Décision Retenue
Il est acté d'intégrer un conteneur dédié à l'incubation de projets au sein de l'arborescence :

1. **Création du Dossier Canonique `PATH_INCUBATION` (`1-Projects/_Incubation/`) :**
   - Ce sous-dossier accueille les projets structurés qui ne sont pas encore engagés dans la phase d'exécution active.
2. **Gestion par Métadonnée YAML `status: someday` :**
   - Tout projet situé dans `_Incubation/` porte la métadonnée `status: someday`.
   - Seuls les projets portant `status: active` et résidant à la racine de `1-Projects/` sont requêtés et affichés par Dataview dans le cockpit exécutif `Home.md`.
3. **Transition Zéro Friction :**
   - Les projets incubés portent déjà le préfixe standard `P-[Nom].md` et leur structure de tâches.
   - Activer un projet consiste en un simple déplacement physique (`mv 1-Projects/_Incubation/P-Nom.md 1-Projects/`) et le passage à `status: active`, sans briser aucun lien existant dans le coffre.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Protection absolue du focus chaud : le cockpit `Home.md` ne présente que les 3 à 5 chantiers prioritaires du moment.
  - Démarrage facilité : les projets en sommeil peuvent être mûris progressivement (ajout de sources, de réflexions) avant leur lancement officiel.
  - Clarté psychologique entre engagement immédiat et désir d'exploration future.
- **Compromis & Contraintes assumés :**
  - Nécessite d'exclure le dossier `_Incubation/` des requêtes Dataview de projets actifs dans les templates et tableaux de bord.

---

## 4. Alternatives Écartées
- **Conserver les projets en sommeil dans l'Inbox :** Rejeté car cela viole le principe de l'Inbox vide (Inbox Zero) et crée de la friction mentale.
- **Note de liste unique "Idées de projets" :** Rejetée car elle empêche de pré-structurer les objectifs, les ressources et les liens d'un chantier d'envergure.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Compétence Dédiée : [[_Arca-BrainOS/skills/Skill_arca-create-note|Skill_arca-create-note (shortcut create-incubation)]]
- Processus de Référence : [[Process-Inbox-Clean-et-Dispatch]]
