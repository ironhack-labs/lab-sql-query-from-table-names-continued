# Rapport — SQL query from table names, continued

## Méthode
Trois nouveaux prompts sont proposés en plus du prompt historique : V1 décrit le schéma avec des instructions SQLite ; V2 ajoute les données de démonstration ; V3 ajoute trois couples question/requête. Les règles et les questions restent identiques pour comparer les représentations du contexte. Les exemples portent sur d’autres questions que les quatre cas évalués, afin de ne pas simplement recopier une réponse fournie. Le prompt historique reste disponible pour comparaison, mais il diffère aussi par ses règles de sortie : il ne constitue donc pas une ablation contrôlée.

La base contient employees, salary et studies, avec clés primaires et étrangères. Cinq employés permettent de tester un salarié sans salaire, un salarié sans études, plusieurs diplômes, deux salaires maximaux ex æquo en 2024 et un ancien salaire plus élevé en 2023. Les dates sont au format ISO. Chaque réponse est exécutée sur une nouvelle base SQLite en lecture seule puis comparée aux lignes attendues, ordre inclus lorsque demandé.

## Résultats effectivement vérifiés
Les quatre requêtes de référence passent : Bob et Carla sont les mieux payés en 2024 ; les nombres de diplômes sont respectivement 1, 1, 2, 0 et 1 ; Emma n’a aucun salaire enregistré ; la moyenne de 2024 est 75 000. Ces résultats proviennent de SQLite, pas d’une génération GPT. Quatre contre-exemples rédigés manuellement montrent des erreurs réelles : ignorer l’année retourne Alice ; LIMIT 1 supprime Carla ; ID_study est une colonne inexistante ; COUNT(*) attribue à Diego une ligne après une jointure externe alors qu’il n’a aucun diplôme.

## Interprétation et limites
L’ancien prompt décrit les colonnes avec des clés incohérentes et un fragment JSON mal formé. Le DDL rend explicites les relations et les noms autorisés. Les lignes d’exemple clarifient les dates et les codes des diplômes. Les exemples SQL peuvent aider à choisir les jointures et les filtres, mais peuvent aussi inciter le modèle à réutiliser une logique inadéquate. Cela reste une hypothèse à mesurer, pas un gain observé ici.

L’expérience API est prête mais n’a pas été exécutée dans cet environnement, qui ne dispose pas du SDK OpenAI configuré. Il faut installer openai et python-dotenv, définir OPENAI_API_KEY et activer RUN_OPENAI pour enregistrer les réponses des trois versions et de l’ancien prompt. Aucun taux de réussite de modèle n’est inventé. Quatre questions sur une seule petite base ne suffiraient de toute façon pas à démontrer une généralisation.

## Ce que je retiens
Une requête valide peut répondre à la mauvaise question. L’année, les ex æquo et les lignes absentes doivent figurer dans la consigne et les données de test. Comparer les résultats est plus pertinent que comparer le style du SQL. Le notebook conserve les sorties et les erreurs pour permettre une analyse reproductible après l’exécution des modèles.

Sources : [étude Text-to-SQL](https://arxiv.org/abs/2305.11853), [API Chat Completions](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/create).

