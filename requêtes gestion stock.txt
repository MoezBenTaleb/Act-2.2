/*insérer des données*/

INSERT INTO `clients` (`id_client`, `nom_client`, `téléphone`, `abonnement`, `intérêt`) VALUES (NULL, 'Moez', '92888888', 'classique', 'sport,musique,');
INSERT INTO `fournisseurs` (`id_fournisseur`, `nom_fournisseur`) VALUES (NULL, 'PUMA');
INSERT INTO `produits` (`id_produit`, `nom_produit`, `type`, `marque`, `référence`) VALUES (NULL, 'ballon', 'matériel football', '', 1);

/*Afficher la liste de tous les clients*/

SELECT * FROM `clients`;

/*Afficher la liste des produits*/

SELECT * FROM `produits`;

/*Afficher les types de produits qui existent dans la BD*/

SELECT type FROM produits;

/*Afficher le nombre de produits disponibles pour chaque type de produit.*/

SELECT type ,COUNT(*) FROM produits GROUP BY type

/*Afficher les infos sur les clients dont le nom des clients 'S'*/

SELECT * FROM `clients` WHERE (`nom_client` LIKE '%S%');

/*Dans la table produits, ajouter une colonne prix.*/

ALTER TABLE `produits` ADD `prix` INT NOT NULL AFTER `référence`;

/*Insérer un prix (égal à 200) dans les lignes déjà existante*/

UPDATE produits SET prix = 200;

/*Afficher pour tous les produits les infos suivantes :nom, type, prix, nom du fournisseur */

SELECT nom_produit, type, prix, nom_fournisseur
FROM produits JOIN fournisseurs ON produits.référence= nom_fournisseur;

/*Afficher le nombre de produit pour chaque fournisseur*/

SELECT nom_fournisseur, COUNT(nom_produit)
FROM produits JOIN fournisseurs ON produits.référence= nom_fournisseur GROUP BY nom_fournisseur;