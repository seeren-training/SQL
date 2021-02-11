# Data definition

*  🔖 **Connection**
*  🔖 **Databases**
*  🔖 **Tables**
*  🔖 **Indexes**

L'objectif de cette section est de définir vos structures de données et d'exécuter nos premières instructions SQL.

___

## 📑 Connection

Le serveur MySql etant démarré vous pouvez établir une connection.

### 🏷️ **Options**

Pour obtenir la liste des options disponibles

```sql
mysqlshow --help
```

### 🏷️ **Instance**

Pour créer une connexion il faut spécifier un nom d'utilisateur et un password. Par défaut le nom d'utilisateur est `root` et le password est vide. Pour spécifier ces informations il faut utiliser les options `-u` et `-p`.

```bash
mysql -u root
```

Dans un terminal autre que linux exécutant un programme window vous aurez une réponse blanche et devez utiliser:

```sql
winpty mysql -u root
```

Vous pouvez spécifier une base de données que vous souhaitez utiliser directement, il en existe déjà comme la base `test`.

```sql
mysql -u root test
```

Pour quitter mysql utilisez `quit` ou `exit`.

```sql
exit
```

___

## 📑 Databases

Une base de données contient des tables.

Nous allons observer comment lister les bases existantes, utiliser, exporter, créer, supprimer une base de données.

### 🏷️ **Lister**

* Obtenir la liste des database existantes

```sql
show databases;
```

### 🏷️ **Utiliser**

* Utiliser une database

```sql
use my_database;
```

### 🏷️ **Exporter**

* Exporter une database

```sql
mysqldump -u root my_database > my_database.sql
```

### 🏷️ **Créer**


Concernant l'identifiant de la base de données il n'y a pas de convention. Seul Microsoft précise une mise en capital de son identifiant, en dehors de ce cadre il est recommandé d'utiliser le snake_case. 

[Create Database](https://dev.mysql.com/doc/refman/5.7/en/create-database.html)

```sql
CREATE DATABASE IF NOT EXISTS my_database;
```

Des options peuvent être spécifiées à la création.

### 🏷️ **Supprimer**

```sql
DROP DATABASE my_database;
```
___

👨🏻‍💻 Manipulation

Créer une database pour votre projet avec une option concernant le CHARACTER SET `utf8` et un COLLLATE `utf8_general_ci`.

___

## 📑 Tables

Une table contient des colonnes.

Nous allons observer comment lister les tables existantes, créer, supprimer, ajouter des options, des contraintes et des attributs.

### 🏷️ **Lister**

Obtenir la liste des tables existantes

```sql
show tables;
```


### 🏷️ **Importer**

Importer les tables dans une base de données

```sql
mysql -u root my_database < my_database.sql
```

### 🏷️ **Créer**

[Create Table](https://dev.mysql.com/doc/refman/8.0/en/create-table.html)

La convention de nommage pour l'identifiant est la même que celle de la database.

* Types et tailles

![image](https://raw.githubusercontent.com/seeren-training/SQL/master/wiki/resources/02/types.jpg)

```sql
CREATE TABLE my_table(
    id INT(10)
);
```

Les colonnes peuvent êtres listées avec la commande suivante.

```sql
show columns from my_table;
```

### 🏷️ **Supprimer**

```sql
DROP TABLE my_table;
```

### 🏷️ **Options**

[Columns](https://dev.mysql.com/doc/refman/8.0/en/columns-table.html)

* Engine

Un table peut utiliser différents moteurs de stokage.

```sql
show engines;
```

Il est spécifiable en option.

```sql
CREATE TABLE my_table(
    foo CHAR(8) NOT NULL
) ENGINE InnoDB;
```

Charset et Collate sont également spécifiables en dans la liste des options.

### 🏷️ **Contraintes et Attributs**

* Default

Une valeur par défaut peut être **contrainte** pour une colonne.

```sql
CREATE TABLE my_table(
    foo CHAR(8) DEFAULT 'my_value'
);
```

* Nullable

Une colonne peut contenir la valeur NULL, pour empêcher ce comportement la **contrainte** NOT_NULL peut être utilisée.

```sql
CREATE TABLE my_table(
    foo CHAR(8) NOT NULL
);
```

* Attributs

La colonne peut posséder les attributs `UNSIGNED`, `BINARY`, `ON UPDATE CURRENT_TIMESTAMP`, `AUTO_INCREMENT`...

```sql
CREATE TABLE my_table(
    foo CHAR(8) UNSIGNED
);
```

___

## 📑 Indexes

Une colonne peut posséder un ou plusieurs indexes. Vous pouvez lister les indexes d'une table avec la commande suivante.

```sql
show indexes from my_table;
```

### 🏷️ **Primary**

Si votre table est grande et importante, mais n'a pas de colonne ou d'ensemble de colonnes évidentes à utiliser comme clé primaire, vous pouvez créer une colonne distincte avec des valeurs d'incrémentation automatique à utiliser comme clé primaire. Ces ID uniques peuvent servir de pointeurs vers les lignes correspondantes dans d'autres tables lorsque vous joignez des tables à l'aide de clés étrangères.

```sql
CREATE TABLE `my_table` (
  id INT PRIMARY KEY
);
```

Il est possible de choisis l'identifiant de l'index.

```sql
CREATE TABLE `my_table` (
  id INT,
  CONSTRAINT id_pk PRIMARY KEY (id)
);
```

### 🏷️ **Unique**

La contrainte UNIQUE garantit que toutes les valeurs d'une colonne sont différentes. Les contraintes UNIQUE et PRIMARY KEY garantissent l'unicité d'une colonne ou d'un ensemble de colonnes. Une contrainte PRIMARY KEY a automatiquement une contrainte UNIQUE. Cependant, vous pouvez avoir plusieurs contraintes UNIQUE par table, mais une seule contrainte PRIMARY KEY par table.

```sql
CREATE TABLE `my_table` (
  id INT UNIQUE
);
```

Il est possible de choisis l'identifiant de l'index.

```sql
CREATE TABLE `my_table` (
  id INT,
  CONSTRAINT id_uk UNIQUE (id)
);
```

### 🏷️ **Index**

Les index sont utilisés pour récupérer les données de la base de données plus rapidement qu'autrement. Les utilisateurs ne peuvent pas voir les index, ils sont juste utilisés pour accélérer les recherches / requêtes.

```sql
CREATE TABLE `my_table` (
  id INT,
  INDEX (id)
);
```

___

👨🏻‍💻 Manipulation

Créer les tables de votre projet en ligne de commande et choisissant avec pertinence les types, les tailles, les options et les indexes.