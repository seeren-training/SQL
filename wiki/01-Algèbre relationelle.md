# Algèbre relationelle

*  🔖 **Base de données relationelles**
*  🔖 **Opérateurs**
*  🔖 **Installation**

___

## 📑 Base de données relationelles

Une base de données permet de stocker de l'information. Une BDD relationelle possède des tables à deux dimensions qui peuvent être reliées. Le langage SQL es utilisé dans la majorité des cas pour les piloter.

![image](https://raw.githubusercontent.com/seeren-training/SQL/master/wiki/resources/01/tables.png)

Ces bases de données sont stockées sur un serveur de base de données relationnelles SQL comme:
* MariaDB
* Microsof SQL server
* Oracle Database
* PostgreSQL
* SQLite

___

## 📑 Opérateurs

Les opérateurs sont utilisés pour rédiger des expressions.

### 🏷️ **Ensemblistes**

* Union: enregistrements de deux relations
* Intersection: enregistrements communs aux deux relations
* Différence: enregistrements d'une table abscent dans la seconde
* Produit cartésien: recopie chaque enregistrements d'une table pour chaque enregistrements d'une autre

### 🏷️ **Relationnels**

* Sélection:  enregistrements vérifiant une condition
* Projection: garde certains attributs des enregistrements
* Rebaptiser: définit un alias
* Jointure: associe plusieurs tables par le biais d’un lien
* Division: ne peut s'exprimmer en SQL

___

## 📑 Installation

Afin de découvrir la syntaxe et utiliser les opérateurs nous allons installer un serveur de base de données relationelle ainsi qu'un client dans une prochaine étape.

### 🏷️ **MariaDB**

Vous trouverez une instance d'une mysql server dans le repertoire `bin`.

[Installation](https://downloads.mariadb.org/)

Pensez à créer le dossier *data* puis installez le serveur.

```sql
mysqld --install
```
Installez les bases de données par défaut

 ```sql
mysql_install_db
```

Installez les utilisateurs par default

```sql
mysqld --initialize-insecure
```

Vous pouvre démarrer votre serveur sans fichiers de configuration par défaut.

```sql
mysqld --no-defaults
```

Pour une distribution configurée vous pouvez installer xampp.

[XAMPP](https://www.apachefriends.org/fr/index.html)

Vérifiez votre installation en démarrant le MySQL serveur:

```sql
mysqld
```

Pour arréter le serveur

```sql
mysqladmin -u root shutdown
```