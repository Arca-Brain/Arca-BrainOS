---
date: "2026-08-09"
title: "ADR-006 : Pipeline de Distillation Découplé en 4 Temps (arca-distill)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-006 : Pipeline de Distillation Découplé en 4 Temps (arca-distill)

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
Dans l'ère de l'abondance informationnelle, capturer des articles, des vidéos YouTube ou des livres tourne presque inévitablement au "syndrome du collectionneur" :
- L'utilisateur stocke des résumés ou des transcriptions qui dorment dans des dossiers sans jamais être relus.
- La connaissance ingérée reste déconnectée du reste du Second Cerveau (notes orphelines sans maillage).
- Aucune passerelle n'existe entre la consommation d'un média et l'action réelle sur les projets en cours.

---

## 2. Décision Retenue
Il est acté de structurer l'ingestion de sources externes sous la forme d'un **pipeline agentique modulaire en 4 temps**, orchestré par le master skill `arca-distill` :

1. **Temps 1 - Synthèse Conceptuelle Pure (`arca-synthesize`) :**
   - Analyse de la matière brute et rédaction d'une note structurée `AI-Distil-[Nom]` dans `2-Ressources/IA-generated/` selon un template rigoureux (thèses, citations marquantes, concepts opératoires, suggestions de wikilinks).
2. **Temps 2 - Ancrage Structurel dans les Thèmes (`arca-converge`) :**
   - Mise à jour des Cartes de Contenu MOCs (`T-`) concernées dans `2-Ressources/Themes/`.
   - Activation des liens suggérés en véritables wikilinks Obsidian actifs.
3. **Temps 3 - Archivage Physique Hors de l'Inbox (`mv`) :**
   - Déplacement immédiat du document brut de `0-Inbox/` vers `2-Ressources/Notes/` pour préserver l'Inbox Zero.
4. **Temps 4 - Analyse d'Impact Projet Proactive (`arca-impact`) :**
   - Scan des projets actifs `P-` et proposition interactive à l'utilisateur de tâches concrètes déduites de la nouvelle connaissance ingérée.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Fin du savoir mort : toute source ingérée est immédiatement assimilée dans le réseau thématique et exploitée au profit des projets réels.
  - Modularité : chaque compétence du pipeline peut être exécutée isolément (ex : relancer `arca-impact` seul).
  - Élimination totale de la corvée de tri et de classement manuel.
- **Compromis & Contraintes assumés :**
  - Nécessite d'exécuter `arca-converge` avec validation si plus de 3 fichiers sont modifiés dans le coffre.

---

## 4. Alternatives Écartées
- **Script monolithique d'ingestion opaque :** Rejeté car il empêche l'inspection humaine des étapes intermédiaires et complique le débogage.
- **Simple résumé IA dans l'Inbox sans convergence :** Rejeté car il maintient la fragmentation et ne crée aucun lien durable avec les MOCs.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Processus de Référence : [[Process-Ingestion-et-Distillation-de-Medias]]
- Compétence Maîtresse : [[_Arca-BrainOS/skills/Skill_arca-distill|Skill_arca-distill]]
