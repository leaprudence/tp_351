
## Description

Cette première partie du projet constitue le lot 1 et se concentre sur la création et la mise en place d'une base de données opérationnelle pour le système de recommandation. 


## Technologies Utilisées

- **Base de données** : PostgreSQL
- **Langage** : Python 
- **Bibliothèques** : Pandas , psycopg2 , os , re

## Fonctionnalités

- Ajout d'articles avec des informations détaillées (titre, année, conférence)
- Gestion des auteurs et de leurs affiliations
- Liens entre articles et auteurs
- Gestion des pays et des villes


### Prérequis

- Python 3.x
- PostgreSQL
- Pip

### Étapes d'installation

1. Clonez le dépôt :

   ```bash
   git clone https://github.com/leaprudence/tp_351.git
   cd tp_351
   
2. Creer un environnement virtuel

   python -m venv env
   source env/bin/activate  # Sur Windows, utilisez `env\Scripts\activate`
   
3. Installez les dépendances 

    pip install -r requirements.txt
 
4. installation des differentes bibliotheques : 
     
     pip install nom_de_la_bibliotheque
     
4. Configurez la base de données :
    Créez une base de données PostgreSQL du nom de 'recsys'
   Modifiez le fichier config.py pour y insérer vos informations de connexion à la base de    données :

		DB_CONFIG = {
		    "dbname": "recsys",
		    "user": "votre_utilisateur",
		    "password": "votre_mot_de_passe",
		    "host": "localhost",
		    "port": "5432"
		}
		
		
		
###### Structure de la base de donnees


Avant d'exécuter le projet, assurez-vous de créer les tables nécessaires dans la base de données `recsys`. Voici les tables requises et leurs structures :

1. Connectez-vous à PostgreSQL :

     psql -U votre_utilisateur -d recsys
Copiez et collez chaque commande SQL ci-dessus dans le terminal après vous être connecté.

	 a.  -- Table pour stocker les affiliations
	CREATE TABLE affiliation (
	    id SERIAL PRIMARY KEY,
	    nom VARCHAR(255) NOT NULL,
	    id_ville INTEGER REFERENCES ville(id)
	);

	b. -- Table pour gérer les relations entre les articles et les auteurs
	CREATE TABLE article_auteur (
	    id SERIAL PRIMARY KEY,
	    id_article INTEGER REFERENCES articles(id),
	    id_auteur INTEGER REFERENCES auteurs(id)
	);

	c. -- Table pour stocker les articles
	CREATE TABLE articles (
	    id SERIAL PRIMARY KEY,
	    titre VARCHAR(255) NOT NULL,
	    annee_publication INTEGER,
	    conference VARCHAR(100)
	);

	d. -- Table pour stocker les informations sur les auteurs
	CREATE TABLE auteurs (
	    id SERIAL PRIMARY KEY,
	    nom VARCHAR(255) NOT NULL,
	    id_affiliation INTEGER REFERENCES affiliation(id)
	);

	e. -- Table pour stocker les informations sur les pays
	CREATE TABLE pays (
	    id SERIAL PRIMARY KEY,
	    nom VARCHAR(255) NOT NULL
	);

	f. -- Table pour stocker les informations sur les villes
	CREATE TABLE ville (
	    id SERIAL PRIMARY KEY,
	    nom VARCHAR(255) NOT NULL,
	    id_pays INTEGER REFERENCES pays(id)
	);
#### utilisation

1. executer le script principale :
          python script.ipynb
  
   
