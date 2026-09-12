---
date: "2026-08-09"
title: "ADR-005 : Cloisonnement Sanctuarisé de l'IA (2-Ressources/IA-generated/) et Intégrité des Écrits Humains"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-005 : Cloisonnement Sanctuarisé de l'IA (2-Ressources/IA-generated/) et Intégrité des Écrits Humains

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
La symbiose entre un être humain et un agent IA au sein d'un Second Cerveau repose sur un contrat de confiance absolu.
Si l'IA dispose de droits d'écriture incontrôlés :
- Elle risque de modifier, écraser ou "reformuler" des réflexions intimes, des récits ou des raisonnements originaux rédigés par l'humain.
- La frontière de provenance devient floue : l'utilisateur ne sait plus ce qui relève de sa propre compréhension et ce qui est de la prose synthétique générée par un LLM.
- Les hallucinations et le jargon creux peuvent contaminer l'ensemble du patrimoine intellectuel du coffre.

---

## 2. Décision Retenue
Il est acté d'instaurer une **ségrégation spatiale stricte des zones d'écriture** et des garde-fous de gouvernance fermes :

1. **Zone d'Écriture EXCLUSIVE pour l'IA (`PATH_IA_GENERATED`) :**
   - Le dossier `2-Ressources/IA-generated/` est sanctuarisé comme le laboratoire de l'IA.
   - C'est la seule zone du coffre où l'IA a l'autorisation d'écrire, de fusionner et de créer des fichiers sans validation humaine préalable (notes préfixées par `AI-Distil-` ou `AI-Synthesis-`).
2. **Sanctuarisation des Notes Humaines :**
   - L'IA a interdiction absolue d'altérer ou de réécrire le contenu rédigé par l'humain dans les projets (`1-Projects/`), les domaines (`3-Domaines-de-vie/`) et les notes personnelles (`2-Ressources/Notes/`).
   - Ses droits d'édition dans les notes humaines sont limités chirurgicalement à :
     - Ajouter des liens sémantiques `[[...]]`.
     - Mettre à jour des cases de tâches (`- [ ]`).
     - Insérer le bloc de journal de bord en bas de note lors de la clôture de session.
3. **Garde-fou des 3 Fichiers Max :**
   - Aucun workflow agentique ne peut créer ou modifier plus de 3 fichiers simultanément sans une confirmation explicite demandée dans le chat.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Sérénité psychologique totale : l'utilisateur sait que ses notes de réflexion personnelle sont inviolables.
  - Hygiène de l'information : séparation limpide entre savoir distillé par l'IA et savoir pensé par l'humain.
  - Révocabilité facile : en cas de dérive d'une synthèse, seule une note isolée dans `IA-generated/` est concernée.
- **Compromis & Contraintes assumés :**
  - Nécessite d'expliciter cette règle de gouvernance en tête de `AGENTS.md` pour contraindre le comportement de n'importe quel LLM.

---

## 4. Alternatives Écartées
- **Co-écriture libre dans les mêmes fichiers :** Rejetée car elle détruit la voix authentique de l'auteur et génère une méfiance permanente envers ses propres notes.
- **Agent en lecture seule intégrale :** Rejeté car il priverait l'utilisateur des gains d'automatisation majeurs sur la synthèse et la tenue des projets.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Constitution du Coffre : [[AGENTS.md (Section Règles de Sécurité & Gouvernance)]]
- Compétence de Synthèse : [[_Arca-BrainOS/skills/Skill_arca-synthesize|Skill_arca-synthesize]]
