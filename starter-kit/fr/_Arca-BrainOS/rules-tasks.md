# ✅ Règles Métier & Cartographie GTD : arca-task-process

> *Ce fichier constitue la mémoire spécialisée (Sidecar Memory) du skill `arca-task-process` (`arca-todo`).*
> *Il stocke la correspondance entre l'ontologie PARA du coffre Obsidian et la structure Todoist de l'utilisateur (Projets, Sections, Labels, Priorités) afin d'automatiser les propositions sans alourdir `memory.md`.*

---

## 🗺️ 1. Cartographie Domaines Obsidian ➔ Structure Todoist (Exemples Personnalisables)

Lors de la première exécution, l'agent découvre automatiquement l'arborescence de votre compte Todoist via l'outil MCP `get-overview` et ajuste ces correspondances selon vos propres listes :

- **Inbox Todoist :** Sas d'entrée mobile à clarifier et vider lors du Volet 2.
- **Todo ❎ (ou Actions Courantes) :**
  - Section **Liste todo** : Cible principale par défaut pour les actions unitaires hors projet (démarches administratives, santé, inscriptions, finances, travail).
  - Section **Un Jour peut-être (Someday/Maybe)** : Idées ou envies sans échéance ferme.
- **Home 🏡 (ou Vie Personnelle) :**
  - Sections : `Routines 🔁`, `2nd brain 🧠`, `Film / Série 📽️`, `Livre 📖`, `Voyage 🚂`, `Read later 📖`.
- **Courses 🛒 (ou Achats) :**
  - Sections : `Supermarché`, `En ville`, `Cadeaux`, `Achat internet`.
- **Make / Travaux 🛠️ :**
  - Sections : `Bricolage`, `Achats matériel`, `Maison travaux`.

---

## 🔄 2. Règles de Frontière Obsidian (`P-`) ⇄ Todoist

1. **Sanctuarisation du Deep Work :**
   - Les tâches d'écriture, d'architecture, de code ou de recherche appartenant aux projets actifs (`1-Projects/P-*.md`) ne sont **jamais** exportées automatiquement dans Todoist.
   - Si une tâche ou réflexion capturée sur mobile dans l'*Inbox Todoist* relève d'un projet `P-` d'Obsidian, l'agent propose au Volet 2 de la **rapatrier dans la note `1-Projects/P-*.md` correspondante** (ou dans `0-Inbox/`) et de la clore dans Todoist.
2. **Actions Externes Ponctuelles liées à un Projet `P-` :**
   - Lorsqu'une tâche d'un projet `P-` nécessite une démarche externe ou en mobilité (appel téléphonique, courrier à poster, achat en magasin) et est envoyée dans Todoist, sa description Todoist contient obligatoirement `[[P-Nom-Projet]]` et la note `P-` conserve le marqueur `⏳ [Todoist]` jusqu'à sa complétion.
3. **Préservation de la Source dans Todoist :**
   - Toute action issue de `0-Inbox/Emails-Actions-Todo.md` emporte sa mention `(Source: ...)` dans le champ `description` de la tâche Todoist avant suppression du fichier tampon.

---

## ⚡ 3. Conventions d'Outils & Priorités (`@doist/todoist-mcp`)

- **Format de priorité :** L'outil `add-tasks` accepte directement les chaînes `"p1"` (priorité maximale, rouge), `"p2"` (haute, orange), `"p3"` (moyenne, bleu) et `"p4"` (normale par défaut, gris).
- **Reprogrammation de dates :** Toujours utiliser l'outil dédié **`reschedule-tasks`** (et jamais `update-tasks`) pour changer la date d'une tâche afin de ne pas détruire les récurrences éventuelles (`Routines 🔁`).

---

## 🧠 Protocole d'Apprentissage Incrémental
1. Dès que l'utilisateur corrige un classement de projet/section Todoist, une priorité ou une habitude de planification lors de la validation du Tableau de Bord Unique, l'agent propose d'inscrire la règle ici.
2. Aucune modification n'est apportée à ce fichier sans validation explicite dans le chat.
