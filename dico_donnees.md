# Dictionnaire des données

## user

|***Champ***|***Type***|***Détails***|***Description***|
|---|---|---|---|
|id|INT|PRIMARY KEY|Identifiant unique de l'utilisateur|
|firstname|TEXT|NOT NULL|Prénom de l'utilisateur|
|lastname|TEXT|NOT NULL|Nom de l'utilisateur|
|email|TEXT|NOT NULL|Adresse mail de l'utilisateur|
|password|TEXT|NOT NULL|Mot de passe de l'utilisateur|
|created_at|TIMESTAMPTZ|NOT NULL DEFAULT now()|Date de création de l'utilisateur|
|updated_at|TIMESTAMPTZ||Date de mise à jour de l'utilisateur|

## quiz

|***Champ***|***Type***|***Détails***|***Description***|
|---|---|---|---|
|id|INT|PRIMARY KEY|Identifiant unique du quiz|
|title|TEXT|NOT NULL|Titre du quiz|
|description|TEXT|NOT NULL|Description du quiz|
|user_id|INT|FOREIGN KEY NOT NULL|Identifiant de l'utilisateur qui a créé le quiz|
|created_at|TIMESTAMPTZ|NOT NULL DEFAULT now()|Date de création du quiz|
|updated_at|TIMESTAMPTZ||Date de mise à jour du quiz|

## level

|***Champ***|***Type***|***Détails***|***Description***|
|---|---|---|---|
|id|INT|PRIMARY KEY|Identifiant unique du niveau|
|nom|TEXT|NOT NULL|Nom du niveau|
|created_at|TIMESTAMPTZ|NOT NULL DEFAULT now()|Date de création du niveau|
|updated_at|TIMESTAMPTZ||Date de mise à jour du niveau|

## question

|***Champ***|***Type***|***Détails***|***Description***|
|---|---|---|---|
|id|INT|PRIMARY KEY|Identifiant unique de la question|
|description|TEXT|NOT NULL|Description de la question|
|anecdote|TEXT||Anecdote de la question|
|wiki|TEXT||Lien vers la page wikipedia de la question|
|quiz_id|INT|FOREIGN KEY NOT NULL|Identifiant du quiz auquel appartient la question|
|answer_id|INT|FOREIGN KEY NOT NULL|Identifiant de la réponse à la question|
|level_id|INT|FOREIGN KEY NOT NULL|Identifiant du niveau de la question|
|created_at|TIMESTAMPTZ|NOT NULL DEFAULT now()|Date de création de la question|
|updated_at|TIMESTAMPTZ||Date de mise à jour de la question|

## answer

|***Champ***|***Type***|***Détails***|***Description***|
|---|---|---|---|
|id|INT|PRIMARY KEY|Identifiant unique de la réponse|
|description|TEXT|NOT NULL|Description de la réponse|
|question_id|INT|FOREIGN KEY NOT NULL|Identifiant de la question à laquelle appartient la réponse|
|created_at|TIMESTAMPTZ|NOT NULL DEFAULT now()|Date de création de la réponse|
|updated_at|TIMESTAMPTZ||Date de mise à jour de la réponse|

## tag

|***Champ***|***Type***|***Détails***|***Description***|
|---|---|---|---|
|id|INT|PRIMARY KEY|Identifiant unique du tag|
|nom|TEXT|NOT NULL|Nom du tag|
|created_at|TIMESTAMPTZ|NOT NULL DEFAULT now()|Date de création du tag|
|updated_at|TIMESTAMPTZ||Date de mise à jour du tag|

## quiz_has_tag

|***Champ***|***Type***|***Détails***|***Description***|
|---|---|---|---|
|quiz_id|INT|FOREIGN KEY|Identifiant du quiz auquel appartient le tag|
|tag_id|INT|FOREIGN KEY|Identifiant du tag auquel appartient le quiz|
