---
date: 2026-06-21
title: "Stop Prompting Claude. Use Karpathy's Method Instead. avec Austin Marchese chez Austin Marchese"
description: "Méthode à 3 couches inspirée d'Andrej Karpathy pour structurer les interactions avec Claude et optimiser les résultats."
tags:
  - YouTube
  - IntelligenceArtificielle
  - ClaudeCode
source: https://www.youtube.com/watch?v=7zZy1QTvokM
---
# 📝 Stop Prompting Claude : La Méthode Karpathy pour Décupler votre Productivité

## ⚡ Résumé
Cette vidéo d'Austin Marchese propose de dépasser le simple 'prompting' traditionnel, qui traite l'IA comme un moteur de recherche, pour adopter une approche d'ingénierie système inspirée d'Andrej Karpathy. À travers un framework en trois couches : la Spécification (Spec), le Scratchpad (mémoire persistante) et la Boucle de Feedback, l'utilisateur structure ses interactions avec Claude comme une collaboration logicielle. Cette méthode permet de guider l'IA avec précision, d'automatiser les vérifications et de capitaliser sur chaque correction pour améliorer le système en continu.

## 💡 Idées Clés
* Dépasser le paradigme du simple prompting [00:00](https://www.youtube.com/watch?v=7zZy1QTvokM&t=0s) : Les utilisateurs traitent souvent l'IA comme un moteur de recherche. Il faut passer à une approche d'ingénierie système pour maximiser l'efficacité.
* Layer 1 : La Spécification (Spec) [00:28](https://www.youtube.com/watch?v=7zZy1QTvokM&t=28s) : Définir des spécifications de tâches précises et collaborer avec l'IA pour valider les objectifs avant d'écrire du code. Cela évite les suppositions erronées de la part du modèle.
* Layer 2 : Le Scratchpad [03:34](https://www.youtube.com/watch?v=7zZy1QTvokM&t=214s) : Utiliser un espace de raisonnement et de mémoire persistant. Cela permet à Claude de garder le contexte des décisions prises entre les différentes sessions de travail.
* Layer 3 : La Boucle de Feedback [08:48](https://www.youtube.com/watch?v=7zZy1QTvokM&t=528s) : Automatiser et pérenniser la correction des erreurs. Au lieu de corriger l'IA de manière ponctuelle, les corrections doivent amender directement les fichiers de spécification ou les règles système.
* Concentrer ses efforts sur la Spec [12:36](https://www.youtube.com/watch?v=7zZy1QTvokM&t=756s) : Si l'on ne doit appliquer qu'une seule règle, c'est de concevoir des spécifications claires. C'est le facteur déterminant pour obtenir des résultats exceptionnels.

## 🗣️ Citations Marquantes
> "Understanding cannot be outsourced."

> "Stop chasing better prompts, start building an architecture that guarantees better outputs."

## 🛠️ Actions Concrètes
* [ ] Rédiger une spécification (Spec) claire et structurée avant de lancer des tâches complexes sur Claude.
* [ ] Créer et maintenir un Scratchpad pour préserver le contexte et le raisonnement au fil des sessions de développement.
* [ ] Mettre en place un processus d'amendement des spécifications dès qu'une erreur de l'IA est corrigée (boucle de feedback).

## 📚 Références & Outils mentionnés
* Livre : "Second Brain" de Tiago Forte
* Outil : Claude Code
* Outil : Obsidian
* Personne : Andrej Karpathy
* Personne : Austin Marchese

## 📝 Résumé détaillé
* Austin Marchese introduit le concept en critiquant la manière dont la majorité des gens utilisent l'IA. Au lieu d'écrire des prompts à la volée comme s'ils effectuaient une recherche Google, ils devraient structurer leur travail. Cette approche, inspirée par Andrej Karpathy, traite les modèles comme Claude comme des agents d'ingénierie logicielle au sein d'un système. [00:00](https://www.youtube.com/watch?v=7zZy1QTvokM&t=0s)
* Le "prompting" classique montre vite ses limites sur des projets complexes car l'IA manque de contexte et doit deviner les intentions profondes de l'utilisateur. En remplaçant le simple prompt par un système structuré, on passe d'une relation d'assistant basique à un véritable partenariat technique où l'IA exécute des tâches avec autonomie et précision. [00:15](https://www.youtube.com/watch?v=7zZy1QTvokM&t=15s)
* La première couche essentielle est la spécification (Spec), qui consiste à définir précisément la tâche à accomplir. Avant que le modèle ne commence à générer du code ou du contenu, l'utilisateur doit rédiger un cahier des charges clair. Cela permet de combler le fossé entre les objectifs abstraits de l'humain et l'exécution rigoureuse de la machine. [00:28](https://www.youtube.com/watch?v=7zZy1QTvokM&t=28s)
* Pour concevoir une bonne spécification, l'auteur conseille de faire "interviewer" l'utilisateur par l'IA elle-même. En posant des questions ciblées sur les objectifs finaux et les contraintes techniques, Claude aide l'humain à clarifier sa vision. Ce processus itératif de co-conception de la spécification garantit que le modèle comprend parfaitement le but recherché. [01:00](https://www.youtube.com/watch?v=7zZy1QTvokM&t=60s)
* Une spécification bien structurée doit être découpée en blocs de tâches agiles et indépendants. Plutôt que de demander à l'IA de réaliser l'ensemble du projet d'un coup, on fragmente le travail avec des jalons clairs. Cela permet de garder le contrôle sur le déroulement et de corriger la trajectoire du modèle avant que des erreurs ne s'accumulent. [01:45](https://www.youtube.com/watch?v=7zZy1QTvokM&t=105s)
* La spécification doit inclure des critères d'acceptation précis pour chaque sous-tâche. En sachant exactement ce qui définit le succès d'une étape, l'IA dispose de repères objectifs pour évaluer son propre travail. La rédaction de la Spec devient ainsi la fondation indispensable sur laquelle reposent les couches suivantes du framework. [02:30](https://www.youtube.com/watch?v=7zZy1QTvokM&t=150s)
* Austin rappelle qu'une bonne spécification n'est pas figée, elle évolue avec le projet. À mesure que des contraintes imprévues surgissent, la Spec est mise à jour, servant de source unique de vérité. C'est ce document qui guide l'IA tout au long de la session, lui évitant d'halluciner ou de dévier des exigences initiales. [03:10](https://www.youtube.com/watch?v=7zZy1QTvokM&t=190s)
* La deuxième couche est le Scratchpad (ou espace de vérification), un outil de persistance pour le raisonnement de l'IA. Lorsque l'on travaille sur de longues sessions, l'IA a tendance à perdre le fil de ses décisions passées à cause de la dérive du contexte. Le Scratchpad sert de mémoire tampon où l'IA note ses plans, l'état actuel des tâches et les décisions architecturales prises. [03:34](https://www.youtube.com/watch?v=7zZy1QTvokM&t=214s)
* Le fonctionnement du Scratchpad s'apparente à une feuille de brouillon structurée que l'IA consulte et met à jour à chaque étape. Ce document contient l'avancement en temps réel, les hypothèses validées et les problèmes restants à résoudre. Cette méthode de pensée à voix haute ("chain-of-thought") améliore considérablement la justesse logique des réponses du modèle. [04:20](https://www.youtube.com/watch?v=7zZy1QTvokM&t=260s)
* Le Scratchpad permet également de mettre en place une auto-vérification systématique. L'IA confronte le résultat de son travail aux critères de la spécification notés sur son brouillon. Si une incohérence est détectée, elle peut la corriger immédiatement avant de soumettre son travail à l'utilisateur, ce qui réduit le nombre d'allers-retours correctifs. [05:10](https://www.youtube.com/watch?v=7zZy1QTvokM&t=310s)
* Pour les développeurs, le Scratchpad est particulièrement puissant lorsqu'il est partagé sous forme de fichier Markdown au sein du projet. Des outils comme Claude Code peuvent lire et modifier directement ce fichier. Cela assure une transition fluide entre les sessions de travail humaines et les exécutions de l'agent IA, qui reprend le projet là où il s'était arrêté. [06:00](https://www.youtube.com/watch?v=7zZy1QTvokM&t=360s)
* Une autre technique consiste à utiliser un modèle secondaire pour auditer le Scratchpad et les résultats produits par le modèle principal. Ce rôle de "vérificateur externe" apporte un regard neuf et impartial. En divisant le travail entre un agent d'exécution et un agent d'audit, la qualité globale du code ou de l'analyse augmente drastiquement. [07:00](https://www.youtube.com/watch?v=7zZy1QTvokM&t=420s)
* L'auteur insiste sur le fait que le Scratchpad libère de la place dans la fenêtre de contexte de l'IA. En synthétisant les informations clés dans un fichier dédié, on évite d'avoir à réinjecter tout l'historique des discussions. C'est une optimisation technique majeure pour garder des réponses rapides et précises de la part de Claude. [08:00](https://www.youtube.com/watch?v=7zZy1QTvokM&t=480s)
* La troisième couche concerne l'environnement dans lequel l'IA évolue, combiné à une boucle de feedback rigoureuse. L'environnement fait référence aux outils, à la structure de fichiers et aux bases de connaissances que l'IA peut consulter. Au lieu de travailler en vase clos, l'agent doit être intégré dans un écosystème d'outils (comme Obsidian ou des wikis de projet) qui lui fournissent le bon contexte au bon moment. [08:48](https://www.youtube.com/watch?v=7zZy1QTvokM&t=528s)
* Un concept clé présenté est l'intégration d'un "LLM Wiki" (ou base de règles). Il s'agit d'un ensemble de fichiers Markdown décrivant les standards de code, les conventions de nommage et les préférences de l'utilisateur. En pointant Claude vers ce wiki, l'IA s'adapte instantanément à la culture de développement du projet sans qu'il soit nécessaire de lui répéter les règles à chaque fois. [09:30](https://www.youtube.com/watch?v=7zZy1QTvokM&t=570s)
* La boucle de feedback intervient lorsqu'un bug ou un comportement indésirable est identifié. Au lieu de simplement corriger l'erreur localement dans le chat ("remplace cette ligne par celle-ci"), l'utilisateur doit corriger le système. Cela signifie mettre à jour la spécification, le Scratchpad ou le LLM Wiki pour s'assurer que cette erreur précise ne se reproduise plus jamais. [10:15](https://www.youtube.com/watch?v=7zZy1QTvokM&t=615s)
* Cette boucle de feedback crée un mécanisme d'apprentissage et d'amélioration continue. Chaque session de travail enrichit l'environnement de l'IA de nouvelles règles et de retours d'expérience documentés. Avec le temps, le système devient de plus en plus résilient et autonome, réduisant l'effort de supervision de l'humain à chaque nouvelle itération. [11:10](https://www.youtube.com/watch?v=7zZy1QTvokM&t=670s)
* Austin montre comment l'utilisation de Claude Code combinée à des scripts de test automatisés complète parfaitement cet environnement. Lorsque l'IA exécute des tests en local, elle reçoit un feedback immédiat de la machine. Ce retour automatisé lui permet de corriger ses propres erreurs en toute autonomie avant de soumettre son travail à la validation humaine. [11:55](https://www.youtube.com/watch?v=7zZy1QTvokM&t=715s)
* Dans la dernière section, Austin résume la leçon principale de ce framework : "l'entendement ne s'externalise pas" (*understanding cannot be outsourced*). L'IA est un outil d'exécution extrêmement puissant, mais l'intelligence de conception et la validation finale doivent rester du ressort de l'humain. L'utilisateur doit se positionner comme l'architecte du système. [12:36](https://www.youtube.com/watch?v=7zZy1QTvokM&t=756s)
* Enfin, il encourage les utilisateurs à se focaliser d'abord et avant tout sur la rédaction de la spécification (Spec) s'ils doivent commencer par un seul élément. Mettre en place cette discipline de clarification préalable est le levier le plus puissant pour transformer Claude d'un chatbot amusant en un collaborateur technique d'élite qui multiplie par dix la vitesse de développement. [13:10](https://www.youtube.com/watch?v=7zZy1QTvokM&t=790s)
