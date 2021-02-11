# Insert and Select

*  🔖 **Insert**
*  🔖 **Transaction**
*  🔖 **Select**
*  🔖 **Clauses**

Vous êtes en ligne de commande, pour visualiser votre structure vous pouvez utiliser ce service en ligne.

🔗 [DBDiagram](https://dbdiagram.io/)

___

## 📑 Insert


[Insert](https://dev.mysql.com/doc/refman/8.0/en/insert.html)

Pour insérer des données dans vos tables il faut utiliser le *Insert Statement*.

### 🏷️ **Inserer une ligne**

Les colonnes qui ne sont pas nullables ou qui ne possèdent pas de valeur par défaut doivent être mises en relation avec une valeur.

```sql
INSERT INTO `client` (
    `id`,
    `name`
) VALUES(
    1,
    'John'
);
```

### 🏷️ **Insérer plusieurs lignes**

En spécifiant plusieurs regroupement de valeurs vous insérez plusieurs lignes.

```sql
INSERT INTO `client` (
    `id`,
    `name`
) VALUES
    (1, 'John'),
    (2, 'Bryan');
```
___

👨🏻‍💻 Manipulation

Insérez des résultats dans une table de type énumération (couleurs, types...).

___

## 📑 Transaction

Prenons le cas de la structure suivante.

```sql
CREATE TABLE `client` (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) UNIQUE
);
CREATE TABLE `address` (
  client_id INT PRIMARY KEY
);
ALTER TABLE address
ADD FOREIGN KEY (client_id)
REFERENCES client(id); 
```

Lors de la création d'une entrée pour ces deux tables sans transaction, si l'insertion de `address` échoue et que l'insertion préalable de client réussit, il y aura un client qui ne possède pas d'adresse.

```sql
INSERT INTO client (`name`) VALUES('John');
INSERT INTO address (`client_id`) VALUES('Bad value');
```

Pour les insertions dans des tables liées, vous devez utiliser la transaction pour exécuter ou annuler l'ensemble des instructions.

```sql
START TRANSACTION;
```

* Tentez vos exécutions.

```sql
INSERT INTO client (`name`) VALUES('John');
INSERT INTO address (`client_id`) VALUES(999);
```

Pour valider les enregistrements il faut engager leur exécution.

```sql
COMMIT;
```

Pour annuler les enregistrements il faut annuler leur exécutions.

```sql
ROLLBACK;
```

En programmation vous utiliserez `COMMIT` en dernière instruction du `try` et `ROLLBACK` en dernière instruction du `catch`.

___

👨🏻‍💻 Manipulation

Tour par tour, insérez des résultats dans deux tables liées en utilisant la transaction. Stockez ces requêtes.

___

## 📑 Select


Pour LIRE des données dans vos tables il faut utiliser le *Select Statement*.

[Select](https://dev.mysql.com/doc/refman/8.0/en/select.html)

### 🏷️ **Tout**

All spécifie toutes les colonnes.

```sql
SELECT * FROM `client`;
```
### 🏷️ **Colonnes spécifiques**

`*` spécifie toutes les colonnes.

```sql
SELECT `id` FROM `client`;
```

### 🏷️ **Fonctions**

Il existe de nombreuses fonctions pour éviter un traitement programmatique.

[Functions](https://dev.mysql.com/doc/refman/8.0/en/group-by-functions.html)

* Compter le nombre de ligne

```sql
SELECT COUNT(`id`) FROM `client`;
```

* Faire un total

```sql
SELECT SUM(`id`) FROM `client`;
```

Utilisé sans opérateurs et sans jointures vous êtes limités à toutes les lignes pour une table.

## 📑 Clauses

Les clauses permettent d'affiner la sélection

[Clause](https://dev.mysql.com/doc/refman/8.0/en/select-optimization.html)

### 🏷️ **Where**

Une condition peut être spécifiée.

```sql
SELECT * FROM `client`
WHERE `id` = 1;
```

* Or

```sql
SELECT * FROM `client` 
WHERE `id` = 1 
OR `name` = 'Kelly';
```

* And

```sql
SELECT * FROM `client` 
WHERE `id` < 10 
AND `name` = 'John';
```

* Like

`%` correspond à n'importe quel aucun ou plusieurs caractères.

```sql
SELECT * FROM `client` 
WHERE `name` LIKE 'J%';
```

`_` correspond à un caractère.

```sql
SELECT * FROM `client` 
WHERE `name` LIKE 'J__n';
```

### 🏷️ **Order by**

* By column

Vous pouvez spécifier plusieurs colonnes en les séparant par une virgule.

```sql
SELECT * FROM `client` ORDER BY `name`;
```

* Ascending

```sql
SELECT * FROM `client` ORDER BY `name` ASC;
```

* Descending

```sql
SELECT * FROM `client` ORDER BY `name` DESC;
```

### 🏷️ **Limit**

Les résultats peuvent être limités.

```sql
SELECT * FROM `client` LIMIT 2;
```

### 🏷️ **Distinct**

Pour ne pas avoir de répétions de valeur il faut utiliser distinct.

```sql
SELECT DISTINCT `name` FROM `client`;
```

### 🏷️ **Group By**

Pour éviter des répétitions tout en prenant en compte les lignes non sélectionnées, groupe by permet de regrouper des résultat. Cette clause est souvent associée à `distinct`.

```sql
SELECT SUM(commande)
FROM client
GROUP BY id
```

___

👨🏻‍💻 Manipulation

Tour par tour, exécutez des sélections qui correspondent à votre logique métier. Stockez ces requêtes.
