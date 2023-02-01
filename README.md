### BDD : Modélisation

> ##### 🫰 Context - concevoir / modéliser une BDD 
>
>- Comment penser l’architecture d'une BDD ?
>- Comment faire pour que les données soient bien organisées ?

#### 📌 La Méthode **MERISE** :

C'est une méthode de conception, de développement et de réalisation de projets informatiques, créée dans les années 70 et très utilisée en France.
Elle s'applique à la modélisation de BDD et permet la séparation des données et des traitements à effectuer en plusieurs modèles conceptuels et physiques.

##### Les modélès de la Méthode MERISE :

- **Modèle Conceptuel de données (MCD)**
Permet d'établir une représentation claire des données et définit les dépendances ***fonctionnelles*** de ces données entre elles. 

- **Modèle Logique de données (MLD)**
Traduction du modèle conceptuel de données en y ajoutant notamment les clés primaires et clés étrangères.

- **Modèle Physique de données (MPD)**
Représentation finale d’une base de données, prenant en compte les spécificités du SGBD (système de gestion de bdd : mysql, postgres, ...) utilisé.

> 🐙 Exemple :
> 
> Nous souhaitons enregistrer les élèves inscrits dans des écoles qui enseignent différents langages.
> 
> Comment organiser ces informations ?
> Comment créer les tables et les champs correspondants ?
>
>
> #### 📌 Première étape le MCD :
> 
> ##### 🎭 Définir les entités :
> 
> Une entité est un regroupement d’éléments ayant les mêmes caractéristiques.
Une entité possède des propriétés permettant de caractériser celle-ci.
Une entité a un identifiant unique.
>
> ![schéma des entités](/assets/img/entités.png "schéma des entités")
>
> ##### 🧑‍🤝‍🧑 Réfléchir aux relations ou associations : 
> C'est le lien entre deux entités.
> Elles ont un nom, souvent un verbe d'action, caractérisant l'action de l'association.
> Une association possède parfois des propriétés.
>
>![associations des entités](/assets/img/associations.png "associations des entités")
>
> Un Student ***est inscrit*** dans une School, une School ***enseigne*** un Language.
>
> ##### 0️⃣ 1️⃣ Poser les cardinalités en fonctions des associations :
> C'est l'indication du nombre min et max de liens entre 2 entités.
> Pour une association de 2 entités, il y a donc 4 cardinalités à indiquer.
> 3 valeurs typiques : 0, 1 et n (plusieurs)
>
>![cardinalités des associations](/assets/img/cardinalités.png "cardinalités des associations")
>  
> Un Student est inscrit dans 1 et 1 seule School
> Dans une School sont inscrits 0 à n Student
> Une School enseigne 1 à n Language
> Un Language est enseigné dans 0 à n School
> ***Résultat final du MCD.***
>
> #### 📌 Deuxième étape, passage du MCD au MLD :
>
> On ne garde que les entités et les cardinalités :
>![mld step 1](/assets/img/mld_step1.png "mld step 1")
>
> Puis on prend les plus grandes cardinalités des deux côtés
pour déterminer le type de relation, 3 possibles :
>- One To One (1, 1)
>- Many To One (1, n)
>- Many To Many (n, m)
>
>![mld step 2](/assets/img/mld_step2.png "mld step 2")
>
> - Lorsqu'il y a une relation **Many To One**, on ajoute une clé étrangère sur la table qui a la cardinalité **1**, celle_ci représente l'id de la table du coté **n**.
>
>![mld step 3](/assets/img/mld_step3.png "mld step 3")
>
> Lorsqu'il y a une relation ***Many To Many***, on crée une table de ***liaison***, ***intermédiaire*** ou de ***jointure*** contenant les ***deux clés étrangères*** des 2 tables (ce couple de clés peut suffire comme clé primaire de la table de jointure mais on pourrait aussi ajouter un champ id auto-incrémenté)
> ***Notons que l'on peut remplacer un des n par un m, pour plus de lisibilité.***
>
>![mld step 4](/assets/img/mld_step4.png "mld step 4")
>
> ***Résultat final du MCD.***
>
>![mld final](/assets/img/mld_final.png "mld final")
>
> #### 📌 Dernière étape, passage du MLD au MPD :
>
> Le niveau physique tient compte des particularités de chaque SGBD.
>- Types des données (INT, VARCHAR, CHAR, BOOL...)
>- Contraintes (unique, nullable, auto-incrémentation...)
>- indexes (amélioration des performances) ...
>
>![mpd schéma](/assets/img/mpd.png "mpd schéma")
>
> #### 📍 Contraintes d'intégrité
>
> Règles à suivre quand des enregistrements de tables reliées sont mis à jour ou supprimés :
>
> Si j'efface une école de la table School, réliée à la table Student, quelle est la règle à suivre ?
> - si aucune contrainte n’est définie, l’école est effacée et les élèves reliés à cette école se retrouvent
alors “orphelins”, leur propriété “school_id” est mise à NULL.
> - si une contrainte est définie sans option, la suppression est refusée car des élèves sont associés à cette école (par contre, on pourra effacer un élève qui lui n’est relié qu’à une et une seule école !)
> - si une option ***CASCADE*** est définie, les élèves associés à l'école supprimée seront automatiquement supprimés également.
> 
> **La règle à suivre pour les contraintes d'intégrité est définie par les spécificités métiers de l’application.**

##### 🪅 Outils et conseils :

📝 Papier et crayon
Rapide et efficace, pour un premier “jet” 🤙

💻 Interfaces graphiques
MySQL Workbench (ou PhpStorm, PhpMyAdmin)...

📡 Solution en ligne QuickDBD:
https://app.quickdatabasediagrams.com/#/


##### 💾 Ressources

[Tutoriel vidéo sur la méthode Merise](https://www.youtube.com/watch?v=XnvNmecmJnE&list=PLbLDQI0AILjJCtQecfOVRx3lqDlmZLLvC)

[Initiation à la méthode Merise](http://ineumann.developpez.com/tutoriels/merise/initiation-merise/) 

[Série de vidéos sur JMerise](https://www.youtube.com/channel/UC-1NsORJux45IQH8LUDcU5A/videos)

#### 🛠 Atelier workshop.md