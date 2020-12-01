# TP3 : Manipulation des grands principes de la cryptographie
## Utilisation de OpenSSL

## Classe : B3B
## Élèves : Emma Durand **[@emmadrd912](https://github.com/emmadrd912)** et Pierre Ceberio **[@PierreYnov](https://github.com/PierreYnov)** 

![](https://static.kinamo.be/upload/sync/headerimg/openssl-commands.png)

# Sommaire 

- [Utilisation d'un algorithme de hachage](#Utilisation-d'un-algorithme-de-hachage)
    - [I. Rappels théoriques](#)
    - [II. Contrôle d'intégrité d'un téléchargement](#)
- [Chiffrement de fichier à l'aide du chiffrement symétrique AES](#)
    - [I. Rappels théoriques](#)
    - [II. Chiffrement de fichier](#)
- [Manipulation des protocoles de chiffrement asymétrique](#)
    - [I. Rappels théoriques](#)
    - [II. Préparation de la biclef](#)
    - [III. Chiffrement et déchiffrement de fichiers](#)
    - [IV. Signature électronique](#)




## Utilisation d'un algorithme de hachage 

### I. Rappels théoriques 

A quoi peut servir une fonction de hachage ?
Si on DL un fichier sur un site, qu'est-ce que le hashage peut permette de prevenir comme risque ?

### II. Contrôle d'intégrité d'un téléchargement 

    - DL GNUPG pour Linux

    - Avec Open SSL, vérifier que l'empreinte SHA1 de l'archive GNUPG est la meme que affichée sur le site ( pas d'alteration pdt le DL)

        (expliquer les manipulations)


## Chiffrement de fichier à l'aide du chiffrement symétrique AES 

### I. Rappels théoriques 

Rappelez les grands principes du chiffrement symétrique.

### II. Chiffrement de fichier 

    - créer un fichier avec du texte dedans
    - chiffrer ce fichier avec Open SSL en utilisant l'algo AES-256-CBC (expliquer les manip)
    - transmettre le fichier et la clef utilisé pour le chiffrement
    - editez le contenu du fichier transmis et constatez qu'il est bien chiffré > Dechiffrer avec la clé obtenu précèdemment (expliquer les manip)
    - vérifier que le contenu obtenu est bien celui rédigé au départ


## Manipulation des protocoles de chiffrement asymétrique 

### I. Rappels théoriques 

Rappellez les 2 application principale chiffrement asymetrique 
Expliquez leurs principes de fonctionnement (expliquer les manip + indiquez les commandes qu'on a utilisé et les commennter)

### II. Préparation de la biclef 

    - générer une paire de clef rsa 2048 
    - Voir ou sont stocke les clé et les sauvegarder

    Quel clé faut il transmettre pour communiquer avec qqun ? 

    - echanger la avec qui voulu

### III. Chiffrement et déchiffrement de fichiers 

    - chiffrer un fichier texte avec la clé donnée 
    - vérifier le contenu et transmetter le a qqun

    - recuperer le fichier chiffrer et dechiffrer

### IV. Signature électronique 

    - signer un fichier texte avec la clé donnée 
    - transmettre le fichier et la signature a qqun

    - recuperer fichier et signature
    - puis dechiffrer à l'aide de la clef et de la signature
    essayer avec une mauvaise clef puis avec la bonne

