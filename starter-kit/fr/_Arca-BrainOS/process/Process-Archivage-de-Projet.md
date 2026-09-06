---
id: "202609061828"
category: Process
date_created: "2026-09-06"
tags:
  - process
  - projet
  - archivage
  - capitalisation
  - gtd
---

# Process : Archivage de Projet & Capitalisation d'Expérience

- **Fréquence :** On Trigger (À l'achèvement ou l'abandon d'un projet actif ou incubé).
- **Déclencheur :** Décision de clôturer définitivement un projet `P-[Nom-Projet]`.
- **Temps actuel :** ~5 min (au lieu de 20 min de manipulations manuelles de fichiers, oubli de clôture dans les Domaines et déperdition des enseignements acquis).

---

## Input
* Note du projet cible `P-[Nom-Projet]` située dans `1-Projects/` (ou `1-Projects/_Incubation/`).
* Journal de bord des sessions antérieures (`## 🪵 Journal de Bord des Sessions`).
* Fiche du ou des Domaines de vie parents (`3-Domaines-de-vie/`).
* Fichier de mémoire opérationnelle (`_Arca-BrainOS/memory.md`).

---

## Étapes

1. **Vérification & Arbitrage des Tâches :**
   - Lancer la commande `arca-archive-project [[P-Nom-Projet]]`.
   - L'agent audite la note pour vérifier qu'aucune tâche importante n'est restée ouverte.
   - Les tâches restantes sont soit cochées (`[x]`), soit rayées (`~[ ]~`), soit converties en idées graines dans le Domaine parent.

2. **Capitalisation Ciblée & Anti-Pollution (Optionnelle) :**
   - L'agent analyse le parcours du projet et formule, si pertinent, 1 ou 2 propositions d'apprentissage :
     - Création d'une note réflexive standard dans `2-Ressources/Notes/` (tag `apprentissage`, reliée à un Thème MOC).
     - Ajout d'une règle récurrente dans `_Arca-BrainOS/memory.md` (soumise au filtre anti-pollution, sans toucher à `AGENTS.md`).
   - L'utilisateur arbitre d'un mot (valider, refuser ou archiver directement).

3. **Scellement & Déplacement Physique :**
   - Les métadonnées du projet sont figées (`status: "completed"`, tag `statut/termine`, horodate finale).
   - Le fichier est déplacé physiquement vers `4-Archives/Projets/` via commande système.

4. **Actualisation des Domaines & Dashboard :**
   - La ligne du projet dans la fiche Domaine parent est annotée avec la mention `(✔ Terminé)`.
   - La table Dataview du Domaine et les compteurs de `Home.md` s'actualisent en temps réel tout en conservant le total des heures et du gain IA cumulé.

---

## Méthode & Critères de Qualité

* **À faire absolument (DO) :**
  * Demander systématiquement la validation humaine explicite avant de déplacer le fichier.
  * Conserver l'intégralité du texte rédigé par l'humain dans la note projet archivée.
  * Préserver la stricte frugalité de `memory.md` (moins de 50 lignes au total).
* **À éviter absolument (DON'T) :**
  * Ne jamais modifier la constitution `AGENTS.md` pour y consigner des apprentissages de projets.
  * Nommer les notes de réflexion ou d'apprentissage de façon naturelle sans préfixe artificiel.
  * Ne pas laisser de projet terminé stagner indéfiniment dans `1-Projects/`.

---

## Output
* Fiche projet scellée et déplacée physiquement dans `4-Archives/Projets/`.
* Éventuelle note de synthèse créée dans `2-Ressources/Notes/` ou règle consignée dans `memory.md`.
* Domaine parent mis à jour (`(✔ Terminé)` et bascule automatique dans la table Dataview des archives).
* Compteurs de santé `Home.md` actualisés en direct.
* Ligne d'archivage unique enregistrée dans `_Arca-BrainOS/log.md`.

---

## 💡 Exemples Concrets d'Exécution & Prompts Types

### Cas 1 : Archivage d'un Projet avec Détection d'Apprentissage
- **Déclencheur Humain (Prompt Utilisateur) :**
  > `arca-archive-project 1-Projects/P-Remboursement-Frais-Medicaux.md`
- **Réponse Agentique (Skill [[Skill_arca-archive-project]]) :**
  > *"Toutes les tâches de P-Remboursement-Frais-Medicaux sont cochées (✔ 165 € perçus).*  
  > *J'ai relevé un apprentissage récurrent : 'Toujours demander le relevé CPAM détaillé avant de relancer la mutuelle'.*  
  > *Souhaites-tu en faire une note réflexive dans Notes/ ou archiver directement ?"*
- **Validation Humaine :**
  > *"Archive directement."*
- **Action Finale :**
  > Déplacement vers `4-Archives/Projets/`, marquage `(✔ Terminé)` dans `Sante.md`, et journalisation dans `log.md`.
