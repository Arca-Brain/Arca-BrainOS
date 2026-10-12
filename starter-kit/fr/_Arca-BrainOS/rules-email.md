# 📬 Règles Métier & Préférences de Tri : arca-email-process

> *Ce fichier constitue la mémoire spécialisée (Sidecar Memory) du skill `arca-email-process`.*
> *Il stocke les règles de routage apprises et les arbitrages d'expéditeurs afin d'automatiser la pertinence des propositions futures sans saturer `memory.md`.*

---

## 🗑️ Lot 1 : Bruit & Archivage Massif (Exemples Paramétrables)

Ces expéditeurs ou types de messages sont automatiquement regroupés dans le Lot 1 pour un archivage immédiat hors de la boîte de réception (`removeLabelIds: ["INBOX", "UNREAD"]`) sans note dans le coffre :

- **Services de mobilité & transport (`*@carsharing-service.com`, alertes sécurité, réservations) :**
  - Action : Archiver hors de la boîte et marquer comme lu.
- **Relevés bancaires & alertes de gestion (`*@ma-banque.fr`, avis de versements périodiques) :**
  - Action : Archiver hors de la boîte et marquer comme lu.
- **Newsletters & Veille commerciale (`*@newsletter-example.com`, courriels promotionnels) :**
  - Action : Toujours archiver et marquer comme lu.
- **E-commerce & Livraisons courantes (notifications de livraison simples) :**
  - Action : Archiver après réception de la notification.

---

## 📚 Lot 2 : Références, Savoir & Veille (Projets, Incubation & Domaines)

Ces emails contiennent des informations, documents ou contacts utiles à conserver sans action immédiate :

- **Documentation & Références Projets :**
  - Comptes-rendus techniques, spécifications ou échanges contractuels rattachables directement à un projet actif (`1-Projects/P-...`) ou en incubation (`1-Projects/_Incubation/P-...`).
  - Action : Intégration sous la section documentation ou ressources du projet concerné, puis archivage de l'email (`removeLabelIds: ["INBOX", "UNREAD"]`).
- **Savoirs transversaux & MOCs :**
  - Articles de fond, benchmarks ou analyses thématiques ➔ Ancrage dans un Thème (`2-Ressources/Themes/T-...`) ou Domaine de vie (`3-Domaines-de-vie/...`).

---

## 🎯 Lot 3 : Next Actions & Engagements (Focus GTD)

Ces emails exigent une action, une réponse ou un suivi :

- **Billets, réservations & bons d'achat (`*@transport-booking.com`, bons de réduction, avoirs) :**
  - Qualification : ⚡ Action unitaire hors projet (utilisation du bon d'achat).
  - Routage : Injection dans `0-Inbox/Emails-Actions-Todo.md`.
  - Action Gmail : Étoile (`STARRED`) et marqué lu.
- **Rendez-vous médicaux & santé (`cabinet@medical-rdv.fr`) :**
  - Qualification : ⚡ Action Santé unitaire hors projet (prise de rendez-vous, suivi ordonnance).
  - Routage : Injection dans `0-Inbox/Emails-Actions-Todo.md`.
  - Action Gmail : Étoile (`STARRED`) et marqué lu.
- **Activités associatives ou sportives régulières :**
  - Qualification : ⚡ Action Santé / Pratique hors projet (ex : stages, cours).
  - Routage : Injection dans `0-Inbox/Emails-Actions-Todo.md`.
  - Action Gmail : Étoile (`STARRED`) et marqué lu.
- **Actions Projets Actifs (`P-`) :**
  - Dès qu'un email concerne un livrable ou un jalon d'un projet actif, l'action est proposée directement pour ce `[[P-...]]`.

---

## 🧠 Protocole d'Apprentissage Incrémental
1. Face à un expéditeur récurrent non répertorié ou un arbitrage inhabituel formulé par l'utilisateur, l'agent demande si la règle doit être enregistrée ici.
2. Une fois validée, l'agent ajoute la règle dans la section adéquate (Lot 1, Lot 2 ou Lot 3) sans modifier `memory.md`.
