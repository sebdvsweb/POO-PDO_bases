# Exercice : Gestion de Personnages avec PDO et POO

## Objectif
Cet exercice a pour objectif de vous familiariser avec la programmation orientée objet (POO) en PHP et l'utilisation de PDO pour interagir avec une base de données. 
Vous allez créer une application simple permettant de gérer des personnages stockés en base de données.

## Étapes à suivre
1. Configuration de la Base de Données
Créez une base de données MySQL et une table pour stocker les personnages. Voici les requêtes SQL pour créer la base de données et la table :

```sql
CREATE DATABASE personnage_db;

USE personnage_db;

CREATE TABLE characters (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    role VARCHAR(100) NOT NULL
);

INSERT INTO characters (name, role) VALUES ('John Doe', 'Guerrier');
INSERT INTO characters (name, role) VALUES ('Jane Smith', 'Mage');
INSERT INTO characters (name, role) VALUES ('Robert Brown', 'Archer');
```

2. Configuration de la Connexion à la Base de Données
Créez un fichier config/database.php pour gérer la connexion à la base de données :


```php
<?php
try {
    $db = new PDO('mysql:host=localhost;dbname=personnage_db;charset=utf8', 'root', '');
    $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    echo 'Échec de la connexion : ' . $e->getMessage();
}
?>
```

3. Autoloading des Classes
Créez un fichier config/autoload.php pour l'autoloading des classes :

```php
<?php
spl_autoload_register(function ($class_name) {
    require_once __DIR__ . '/../class/' . $class_name . '.php';
});
?>
```

4. Création de la Classe Personnage
Créez un fichier class/Personnage.php et définissez la classe Personnage avec les propriétés nécessaires : `$id`, `$name`, `$role`
Ajouter les getters et setters et les méthodes Save() et getAll() pour modifier ou sélectionner les personnages dans la base de données.

5. Création de la Page d'Index
Créez un fichier index.php à la racine de votre projet pour afficher et gérer les personnages.
Y inclure les fichiers nécessaires avec PHP : `require './config/database.php';` et `require './config/autoload.php';`



