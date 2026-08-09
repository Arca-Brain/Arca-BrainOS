---
id: "202607172327"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - rag
  - recherche
  - ia
---
# Process : Exploration Sémantique & Recherche Augmentée

- **Fréquence** : On Trigger (À la demande, lors d'une réflexion créative ou d'un besoin d'exploration).
- **Déclencheur** : Questionnement complexe, besoin de synthétiser des connaissances éparses ou préparation d'un projet/écrit.

---
## Input
* Question ou thématique d'exploration posée par l'humain.
* Notes distillées (`AI-Distil-`), notes de leçons (`L-`) et sources brutes dans le Vault.

## Étapes
1. **Poser la requête d'exploration** : Lancer la commande `arca-query` suivie de la question ou du sujet d'exploration.
2. **Scan croisé & Triage sémantique** : L'IA croise le savoir déjà distillé (`AI-Distil-`), les notes de projet `P-`, et les sources brutes en attente dans l'Inbox.
3. **Restituer la cartographie des connaissances** : L'IA génère un bilan synthétique interactif dans le chat exposant :
   - Ce que le Second Cerveau sait déjà (acquis).
   - Les ponts sémantiques entre idées distantes.
   - Les trous de connaissances (*gaps* et questions ouvertes).
4. **Approfondir (Optionnel)** : Utiliser les skills de recherche pour traverser le graphe de liens ou faire une recherche web complémentaire.
5. **Capitaliser l'insight (Optionnel)** : Si l'exploration débouche sur une intuition majeure, l'enregistrer sous forme d'une note de leçon `L-` ou d'un brouillon d'écrit.

## Méthode & Critères de Qualité
* **Structure requise** : La commande `arca-query` doit rester strictement **conversationnelle et informative** sans altérer les MOCs ni écrire dans `log.md` (anti-pollution).
* **À faire absolument (DO)** :
  * Citer explicitement les notes sources du Vault avec leurs wikilinks `[[...]]`.
  * Révéler les connexions inattendues entre des domaines différents.
* **À éviter absolument (DON'T)** :
  * Ne pas modifier de fichiers dans le Vault lors d'une simple requête d'exploration.
  * Ne pas inventer d'informations non présentes dans les notes sans le préciser.

## Output
* Synthèse sémantique interactive dans le chat.
* Détection des lacunes et opportunités de maillage.
* (Optionnel) Nouvelle note d'ébauche ou de leçon créée dans l'Inbox.

## Exemples
* Session d'exploration croisée sur le lien entre l'IA agentique, l'anthropologie et la mémoire étendue.

## Douleurs principales
* "Amnésie du Second Cerveau" : Avoir pris des dizaines de notes mais être incapable de les retrouver et de les connecter au moment d'écrire.
* Temps perdu à chercher manuellement des mots-clés sans bénéficier du rapprochement sémantique par IA.

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Expression de la question** | **Humain** | Reformulation claire de l'intention d'apprentissage. | **Formuler** la question ou le problème complexe. | 🟢 (Opérationnel) |
| **2. Scan RAG & Triage sémantique** | **Agent IA** | Commande `arca-query` (RAG hybride Vault + Inbox). | **Aucun** : Calcul sémantique automatique par l'IA. | 🟢 (Opérationnel) |
| **3. Restitution & Ponts cognitifs** | **Agent IA** | Synthèse structurée, citation de notes et détection des gaps. | **Évaluation** : Apprécier la valeur des connexions proposées. | 🟢 (Opérationnel) |
| **4. Décision de capitalisation** | **Humain** | Décision de transformer l'insight en note permanente. | **Arbitrage** : Choisir d'ancrer ou non l'ébauche. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Curiosité & Intention créative** : L'IA ne cherche rien d'elle-même ; la question de départ et l'angle d'attaque viennent de l'humain.
* **Discernement & Étincelle créative** : L'IA propose des ponts sémantiques, mais seul l'humain ressent si une connexion fait "tilt" pour ses projets.
* **Sanctuarisation sans pollution** : Ce processus est 100% conversationnel pour protéger l'intégrité de la structure du Vault.

**Pipeline complet** : Question (Humain) ➔ `arca-query` (Agent IA RAG) ➔ Restitution sémantique ➔ Synthèse & Décision d'ancrage (Humain).
