# Update and Delete

*  🔖 **Update**
*  🔖 **Delete**
*  🔖 **Imbrication**

___

## 📑 Update

Vous pouvez mettre à jour vos résultats en utilisant le *Update Statement*.

🔗 [Update](https://dev.mysql.com/doc/refman/8.0/en/update.html)

### 🏷️ **Modifier plusieurs lignes**

Pour modifier plusieurs colonnes, séparez les colonnes et affections par des virgules.

```sql
UPDATE `client` SET id = id + 10;
```

### 🏷️ **Modifier une ligne**

```sql
UPDATE `client` SET name = "Foo" 
WHERE name = 'John';
```
___

## 📑 Delete


Vous pouvez mettre à jour vos résultats en utilisant le *Update Statement*.

🔗 [Delete](https://dev.mysql.com/doc/refman/8.0/en/delete.html)

### 🏷️ **Supprimer plusieurs lignes**

Pour modifier plusieurs colonnes, séparez les colonnes et affections par des virgules.

```sql
DELETE FROM `client`;
```

### 🏷️ **Supprimer une ligne**

```sql
DELETE FROM `client`;
WHERE name = 'Foo';
```
___

## 📑 Imbrication

Les opérations sont souvent dépendantes de sous opérations de lecture notamment. Vous souhaitez par exemple mettre à jour une ligne de résultat qui dépend d'un résultat de lecture d'une autre.

```sql
UPDATE `client` SET name = 'Last' 
WHERE id = (
    SELECT id FROM client
    ORDER BY id DESC LIMIT 1
);
```

### 🏷️ **In**

L'opérateur In permet de mettre une condition de présence dans une liste de valeur.

```sql
UPDATE `client` SET id = id + 100
WHERE id IN (
    SELECT id FROM client
    WHERE id < 100
);
```
___

👨🏻‍💻 Manipulation

Tour par tour, exécutez des mise à jour et suppression qui correspondent à votre logique métier. Stockez ces requêtes.
