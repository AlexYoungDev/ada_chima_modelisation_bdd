### Modéliser une base de données

Nous allons opter de modéliser notre base de données en trois étapes : <br> 
- le Modèle Conceptuel de données (MCD - Verbes) 
- le Modèle Logique de données (MLD - Cardinalités)
- le Modèle Physique de données (MPD - Relations)

#### 🐶 Contexte

> Chaque année, notamment lors de la saison estivale, de nombreux animaux sont abandonnés par leurs maîtres. <br>
> La SPA a pour mission de les recueillir au sein de l'un de ses 63 refuges. Ils sont pris en charge par les équipes puis identifiés, stérilisés, vaccinés, soignés, éduqués et sociabilisés avant d’être proposés à l’adoption.
> <br>
Vous avez un grand coeur, c'est pourquoi vous vous rendez dans l'un de ces refuges pour adopter l'une ou plusieurs de ces petites bêtes.


#### 🛠 Atelier

Vous devez modéliser avec succès le MCD puis le MLD de la base de données du site de la SPA. 

Je te recommande de le faire à l'aide d'un crayon et d'une feuille de papier.

Un animal est renseigné par un ***nom***, une ***déclinaison***, un ***âge*** estimé, ainsi qu'un ***numéro de puce***.

Il faut aussi pouvoir dire si un animal a été ***stérilisé*** ou non. De même pour les ***vaccins obligatoires***.
Une déclinaison (labrador, maine coon, ...) est associée à une espèce (chat, chien, ...)
Un **adoptant** doit fournir quelques renseignements (***prénom, nom, date de naissance*** et ***adresse***)

À noter qu'un adoptant peut adopter un ou plusieurs animaux. 


#### 🦄 Contexte, la suite

Maintenant que la base de données est conçue, il s'avère que toutes les SPA veulent s'en servir ! Quel succès 💛

Ton grand coeur te perdra car tu ne peux pas refuser cette mission,  te voilà obligé de faire évoluer ton modéle....

#### 🚀 Atelier, la suite

Un animal est recueilli par un refuge de la SPA.
Chaque adoption doit faire l'objet d'un enregistrement avec une date et une heure.