# 📜 Registre des Décisions d'Architecture (ADR - Arca-BrainOS)

> *Ce dossier héberge l'ensemble des Architectural Decision Records d'Arca-BrainOS selon le modèle standard [[Template-ADR]].*
> *Chaque décision fige un arbitrage structurant pour garantir la pérennité du système et prévenir toute régression future.*

---

### 🏛️ Socle Fondateur v1.0.0 (Rétro-Documenté)

1. [[ADR-001-Portabilite-et-Souverainete-LLM-Agnostique]] : *Portabilité absolue et souveraineté LLM-agnostique (du cloud souverain au 100% local privé via Ollama).*
2. [[ADR-002-Architecture-Decouplee-Moteur-vs-Coffre]] : *Architecture découplée en 2 parties étanches (`_Arca-BrainOS/` vs coffre souverain de l'utilisateur).*
3. [[ADR-003-Ontologie-PARA-Decouplee-au-Write-Time]] : *Ontologie relationnelle au Write-Time (`P-`, `T-`, `Area`) vs dossiers hiérarchiques rigides et RAG naïf.*
4. [[ADR-004-Incubation-GTD-et-Preservation-du-Focus]] : *Sas d'incubation GTD (`1-Projects/_Incubation/`, `status: someday`) pour protéger le focus actif.*
5. [[ADR-005-Cloisonnement-Sanctuarise-Zone-IA]] : *Sanctuarisation de la zone d'écriture IA (`2-Ressources/IA-generated/`) et inviolabilité des notes humaines.*
6. [[ADR-006-Pipeline-Distillation-Decouple-en-4-Temps]] : *Pipeline de distillation modulaire en 4 temps (`arca-distill`) reliant la veille à l'action projet.*
7. [[ADR-007-Dichotomie-Projets-Intellectuels-vs-Monde-Reel]] : *Qualification séparée des projets intellectuels (`themes: [...]`) et des projets du monde réel (`themes: []`).*
8. [[ADR-008-Protocole-Deep-Work-et-Bilan-ROI-Temporel]] : *Encadrement rituel des sessions (`arca-resume`, `arca-close-session`) et mesure mathématique du gain de temps.*
9. [[ADR-009-Modele-Memoire-Frugale-CoALA-4-Niveaux]] : *Architecture de mémoire étagée en 4 strates textuelles frugales (`_Arca-BrainOS/memory.md` < 50 lignes).*
