# Jointure

*  🔖 **Definition**
*  🔖 **Join**

___

## 📑 Definition

🔗 [join](https://dev.mysql.com/doc/refman/8.0/en/join.html)

Dans la cadre de tables en relations, la jointure permet de faire une selection sur plusieurs tables.

![image](https://raw.githubusercontent.com/seeren-training/SQL/master/wiki/resources/05/jointure.jpg)

___

## 📑 Join

MySql ne possède pas de outer join. Son équivalent correspond à une union entre un left et right join.

### 🏷️ **Inner**

```sql
SELECT * from client
JOIN address 
ON client.id = address.client_id;
```

### 🏷️ **Left**

```sql
SELECT * from client
LEFT JOIN address 
ON client.id = address.client_id;
```

### 🏷️ **Right**

```sql
SELECT * from client
RIGHT JOIN address 
ON client.id = address.client_id;
```

### 🏷️ **Outer**

```sql
SELECT * from client
LEFT JOIN address 
ON client.id = address.client_id
UNION
SELECT * from client
RIGHT JOIN address 
ON client.id = address.client_id;
```

___

👨🏻‍💻 Manipulation

Tour par tour, exécutez des sélections qui correspondent à votre logique métier. Stockez ces requêtes.

___

Nous avons passé en revue la syntaxe necessaire à la manipulation de donnée avec un langage de programmation. Il est temps de passer à la programmation et de vous référez quand il le faut à cette base syntaxique pour forger vos requêtes.