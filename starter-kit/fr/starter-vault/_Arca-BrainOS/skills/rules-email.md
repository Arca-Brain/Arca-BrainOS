# 📬 Règles Métier & Préférences de Tri : arca-email-process

> *Ce fichier constitue la mémoire spécialisée (Sidecar Memory) du skill `arca-email-process`.*
> *Il stocke les règles de routage apprises et les arbitrages d'expéditeurs afin d'automatiser la pertinence des propositions futures sans saturer `memory.md`.*

---

## 👤 Règles par Expéditeur & Routage Établi (Modèles à adapter)

- **Services Administratifs & Banques (`*@ma-banque.fr`, avis de versements, relevés) :**
  - Catégorie GTD : 📚 Information administrative.
  - Action Vault : Ne pas créer de note unitaire (sauf demande explicite).
  - Action Gmail : Archiver hors de la boîte de réception et marquer comme lu (`removeLabelIds: ["INBOX", "UNREAD"]`).

- **Billets de Transport, Réservations & Avoirs (`*@compagnie-train.fr`, billets, retards) :**
  - Catégorie GTD : 🎫 Suivi & Justificatif.
  - Action Vault : Consigner la référence et la date dans la note récapitulative `0-Inbox/Triage-Emails-AAAA-MM-JJ.md` rattachée au Domaine `[[Voyage]]` ou `[[Personnel]]`.
  - Action Gmail : Conserver dans la boîte de réception avec Étoile (`addLabelIds: ["STARRED"]`, `removeLabelIds: ["UNREAD"]`).

- **Rendez-vous Médicaux & Santé (`*@docteur.fr`, rappels de consultation) :**
  - Catégorie GTD : ⚡ Action Santé.
  - Action Vault : Consigner dans la note récapitulative `0-Inbox/Triage-Emails-AAAA-MM-JJ.md` rattachée au Domaine `[[Sante]]`.
  - Action Gmail : Conserver dans la boîte de réception avec Étoile (`addLabelIds: ["STARRED"]`, `removeLabelIds: ["UNREAD"]`).

- **Direction & Équipe Projet (`direction@entreprise.com`, arbitrages stratégiques) :**
  - Catégorie GTD : ⚡ Action Projet.
  - Action Vault : Injecter la tâche directement dans le projet actif concerné (`1-Projects/P-...`).
  - Action Gmail : Conserver dans la boîte de réception avec Étoile (`addLabelIds: ["STARRED"]`, `removeLabelIds: ["UNREAD"]`).

---

## 🛡️ Règles Générales de Filtrage
- **Newsletters, Promotions & Bruit commercial :** Toujours archiver et marquer comme lu (`removeLabelIds: ["INBOX", "UNREAD"]`).
