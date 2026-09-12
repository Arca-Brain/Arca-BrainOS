---
date: "2026-08-09"
title: "ADR-008 : Protocole de Deep Work Borné et Bilan de ROI Temporel (arca-resume & arca-close-session)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-008 : Protocole de Deep Work Borné et Bilan de ROI Temporel (arca-resume & arca-close-session)

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
Collaborer avec des copilotes et agents IA engendre souvent deux dérives perverses :
- **L'errance cognitive :** Ouvrir une session sans objectif clair et se laisser porter par des conversations digressives sans livrable concret à l'arrivée.
- **L'illusion d'efficacité :** Ressentir une impression de vitesse sans être capable de mesurer rationnellement si l'IA a réellement économisé du temps ou si elle a généré du temps perdu en réécritures et prompts stériles.

---

## 2. Décision Retenue
Il est acté de sanctuariser chaque bloc de travail sous la forme d'un **protocole de Deep Work rigoureusement borné**, outillé par deux compétences maîtresses :

1. **Le Rituel d'Ouverture (`arca-resume`) :**
   - Charge la mémoire opérationnelle (`_Arca-BrainOS/memory.md`).
   - Scanne la note de projet cible `1-Projects/[P-Nom].md` et rappelle les derniers jalons franchis.
   - Force l'alignement immédiat : l'IA propose une intention de session, liste les tâches cibles et initialise le journal de travail.
2. **Le Rituel de Clôture & ROI Temporel (`arca-close-session`) :**
   - Réorganise les tâches réalisées (`- [x]`) et restantes (`- [ ]`).
   - Calcule le **Bilan Temporel & Productivité IA** selon une métrique objective :
     - *Temps humain réel investi* (durée du bloc de concentration).
     - *Estimation sans IA* (durée d'exécution manuelle réaliste).
     - *Temps net économisé* et *Multiplicateur d'accélération* (ex : x3.5).
   - Injecte le bloc de journal de bord indélébile en bas du projet `P-` (`## 🪵 Journal de Bord des Sessions`).
   - Déclenche la sauvegarde Git adaptative (locale ou NAS).

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Mesure empirique du ROI de l'IA (prouvé sur plus de 35 sessions et +190h économisées).
  - Reprise de contexte instantanée lors des sessions suivantes (zéro amnésie).
  - Discipline de travail : clôturer formellement une session évite de laisser des tâches en suspens.
- **Compromis & Contraintes assumés :**
  - Nécessite d'estimer avec honnêteté le temps de travail manuel de référence pour préserver la rigueur des statistiques.

---

## 4. Alternatives Écartées
- **Outils SaaS externes de time-tracking (Toggl, Clockify) :** Rejetés car ils fragmentent l'attention et ne lient pas le temps investi au texte même des notes.
- **Sessions de chat volatiles sans clôture :** Rejetées car elles dispersent la mémoire du projet dans des historiques de conversation éphémères.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS (Statistiques globales en en-tête)]]
- Processus de Référence : [[Process-Pilotage-de-Projets-et-Deep-Work]]
- Compétences Associées : [[_Arca-BrainOS/skills/Skill_arca-resume|Skill_arca-resume]] & [[_Arca-BrainOS/skills/Skill_arca-close-session|Skill_arca-close-session]]
