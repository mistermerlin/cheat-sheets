
# Introduction à SQL (Structured Query Language)

## Qu'est-ce que SQL ?

SQL, ou Structured Query Language, est un langage de programmation standardisé conçu pour la gestion et la manipulation des bases de données relationnelles. Il offre un moyen uniforme d'interagir avec différentes bases de données, permettant de créer, récupérer, mettre à jour et supprimer des données.

## Bases de données relationnelles

Les bases de données relationnelles sont des systèmes de gestion de bases de données (SGBD) basés sur le modèle relationnel, où les données sont organisées en tables. Chaque table est composée de lignes et de colonnes, et chaque ligne représente un enregistrement unique.

## MySQL

MySQL est l'un des systèmes de gestion de base de données relationnelles les plus populaires, largement utilisé pour son efficacité, sa simplicité et sa compatibilité open source.

# Principales commandes SQL

### 1. Création de la base de données :

```sql
CREATE DATABASE IF NOT EXISTS bibliotheque;
```

### 2. Sélection de la base de données :

```sql
USE bibliotheque;
```

### 3. Création d'une table pour les livres :

```sql
CREATE TABLE IF NOT EXISTS livres (
    id INT AUTO_INCREMENT PRIMARY KEY,
    titre VARCHAR(255) NOT NULL,
    auteur VARCHAR(255) NOT NULL,
    annee_publication INT
);
```

### 4. Insertion de données dans la table des livres :

```sql
INSERT INTO livres (titre, auteur, annee_publication) VALUES 
('Le Seigneur des Anneaux', 'J.R.R. Tolkien', 1954),
('Harry Potter à l\'école des sorciers', 'J.K. Rowling', 1997),
('1984', 'George Orwell', 1949);
```

### 5. Sélection de tous les livres publiés après 1950 :

```sql
SELECT * FROM livres WHERE annee_publication > 1950;
```

### 6. Mise à jour de l'auteur du premier livre :

```sql
UPDATE livres SET auteur = 'John R.R. Tolkien' WHERE id = 1;
```

### 7. Suppression du livre publié en 1949 :

```sql
DELETE FROM livres WHERE annee_publication = 1949;
```

### 8. Sélection de tous les livres avec tri par année de publication :

```sql
SELECT * FROM livres ORDER BY annee_publication;
```

### 9. Jointure avec une autre table (supposons une table pour les genres) :

```sql
CREATE TABLE IF NOT EXISTS genres (
    id INT AUTO_INCREMENT PRIMARY KEY,
    genre_nom VARCHAR(255) NOT NULL
);

INSERT INTO genres (genre_nom) VALUES ('Fantasy'), ('Science Fiction'), ('Dystopie');

SELECT livres.titre, livres.auteur, genres.genre_nom 
FROM livres 
INNER JOIN genres ON livres.id_genre = genres.id;
```

### 10. Agrégation pour compter le nombre de livres par auteur :

```sql
SELECT auteur, COUNT(*) AS nombre_de_livres 
FROM livres 
GROUP BY auteur;
```
