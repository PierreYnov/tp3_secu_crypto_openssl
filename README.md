# TP3 : Manipulation des grands principes de la cryptographie
## Utilisation de OpenSSL

## Classe : B3B
## Élèves : Emma Durand **[@emmadrd912](https://github.com/emmadrd912)** et Pierre Ceberio **[@PierreYnov](https://github.com/PierreYnov)** 

![](https://static.kinamo.be/upload/sync/headerimg/openssl-commands.png)

# Sommaire 

- [Utilisation d'un algorithme de hachage](#utilisation-dun-algorithme-de-hachage)
    - [I. Rappels théorique](#i-rappels-th%C3%A9orique)
    - [II. Contrôle d'intégrité d'un téléchargement](#ii-contr%C3%B4le-dint%C3%A9grit%C3%A9-dun-t%C3%A9l%C3%A9chargement)
- [Chiffrement de fichier à l'aide du chiffrement symétrique AES](#chiffrement-de-fichier-%C3%A0-laide-du-chiffrement-sym%C3%A9trique-aes)
    - [I. Rappels théorique](#i-rappels-th%C3%A9orique-1)
    - [II. Chiffrement de fichier](#ii-chiffrement-de-fichier)
- [Manipulation des protocoles de chiffrement asymétrique](https://github.com/PierreYnov/tp3_secu_crypto_openssl#manipulation-des-protocoles-de-chiffrement-asym%C3%A9trique)
    - [I. Rappels théorique](#i-rappels-th%C3%A9orique-2)
    - [II. Préparation de la biclef](#ii-pr%C3%A9paration-de-la-biclef)
    - [III. Chiffrement et déchiffrement de fichiers](#iii-chiffrement-et-d%C3%A9chiffrement-de-fichiers)
    - [IV. Signature électronique](#iv-signature-%C3%A9lectronique)




## Utilisation d'un algorithme de hachage 

### I. Rappels théorique 

**À quoi peut servir une fonction de hachage ?**

À signer un fichier, créer une empreinte numérique, un hash. 

**Si on télécharge un fichier sur un site, quel risque peut-elle prévenir ?**

Elle peut prévenir la falsification d'un fichier, pour pouvoir garantir son intégrité. On peut comparer le hash donné sur le site avec celui du fichier téléchargé.

### II. Contrôle d'intégrité d'un téléchargement 

    - DL GNUPG pour Linux

    - Avec Open SSL, vérifier que l'empreinte SHA1 de l'archive GNUPG est la même que celle affichée sur le site (pas d'altération pendant le téléchargement)

Je télécharge le fichier ``gnupg``, sur son site, puis je compare sa signature ``SHA1`` avec celle notée sur le site (``openssl sha1 gnupg-2.2.25.tar.bz2``), ce sont les mêmes :

![](https://i.gyazo.com/96271da791d9d4d5b7d933399080b99e.png)

On retrouve la même empreinte SHA1 ``074b21dd07419575fa31c0c5d3116596d5544cbd``

## Chiffrement de fichier à l'aide du chiffrement symétrique AES 

### I. Rappels théorique

**Rappelez les grands principes du chiffrement symétrique.**

Consiste à chiffrer et déchiffrer un contenu avec la même clef secrète et le même algo. L'émetteur et le destinataire doivent se mettre d'accord sur la clef secrète.

### II. Chiffrement de fichier 

    - créer un fichier avec du texte dedans
    - chiffrer ce fichier avec Open SSL en utilisant l'algo AES-256-CBC (expliquer les manipulations)
    - transmettre le fichier et la clef utilisé pour le chiffrement
    - éditez le contenu du fichier transmis et constatez qu'il est bien chiffré > Déchiffrer avec la clé obtenue précédemment (expliquer les manipulations)
    - vérifier que le contenu obtenu est bien celui rédigé au départ

On crée le fichier :

![](https://i.gyazo.com/6e919e1795af27abecd3c444277903af.png)

Sa signature :

![](https://i.gyazo.com/310bd0800683c9c7da8424c736e00716.png)

Pour chiffrer en ``AES-256-CBC`` on utilise la commande suivante : 
![](https://i.gyazo.com/489922dcf04a921cd423f4f96091a165.png)

Emma reçoit le fichier et édite son contenu pour constater le chiffrement du fichier : 

![](https://i.gyazo.com/9acc9293b616f15ee207ac4909187245.png)

Il faut maintenant déchiffrer avec cette commande :

![](https://i.gyazo.com/d1ef27ef086017bf695b7ede23c13eb0.png)

Le contenu est le même, mais pour garantir son intégrité on vérifie avec son empreinte ``SHA1`` :

![](https://i.gyazo.com/360cd330d0f11fed6e0689437c3d5735.png)

C'est le même ! 

## Manipulation des protocoles de chiffrement asymétrique 

### I. Rappels théorique

**Rappelez les 2 applications principales du chiffrement asymétrique. Expliquez leurs principes de fonctionnement**

Les deux applications principales sont :

- Chiffrement : Alice chiffre son message avec la clef publique de Bob et Bob déchiffre ce message avec sa propre clé privée 
- La signature électronique : Alice chiffre son message avec sa propre clef privée, elle envoie le message + la signature à Bob, Bob déchiffre la signature avec la clef publique de Alice.

### II. Préparation de la biclef 

    - générer une paire de clef rsa 2048 
    - Voir ou sont stocke les clés et les sauvegarder

    Quelle clé faut-il transmettre pour communiquer avec quelqu'un ? 

    - échanger la 

Je génère ma clé privée en ``rsa 2048``, dans le fichier ``private.pem``, en inscrivant une pass-phrase :

![](https://i.gyazo.com/d3e08b8f9b61086f871b36978a898acc.png)

Le fichier est créé dans le répertoire où je me situais dans le terminal.

Je génère ensuite la clé publique dans le fichier ``public.pem`` :

![](https://i.gyazo.com/f0239c39ebdcef58a21293d378a158bc.png)

Les fichiers sont bien créés 

![](https://i.gyazo.com/b433ffde6334e7f4603391d115abb81c.png)

Il faut transmettre sa clé publique pour communiquer avec un interlocuteur.

Je donne donc ma clé publique à Emma.

### III. Chiffrement et déchiffrement de fichiers 

    - chiffrer un fichier texte avec la clé donnée 
    - vérifiez le contenu et transmettez-le à quelqu'un

    - récupérer le fichier chiffré et dechiffré

Je chiffre avec la clef publique de Emma :

![](https://i.gyazo.com/b5af7e52a4aaf210d11f1745df5e881a.png)

Je ``cat`` pour constater le chiffrement du fichier. C'est fonctionnel. 

Je lui transmets. Elle va donc déchiffrer le fichier avec sa clef privée et vérifier le contenu originel :

![](https://i.gyazo.com/0a3f6c6324e1f9e1911b0e1a6f6c3eb0.png)

### IV. Signature électronique 

    - signer un fichier texte avec la clé donnée 
    - transmettre le fichier et la signature à quelqu'un
    - recuperer fichier et signature
    - puis déchiffrer à l'aide de la clef et de la signature
    essayer avec une mauvaise clef puis avec la bonne



Je signe le fichier texte avec ma clé privée, en ``SHA1``. La signature est dans le fichier ``sha1.sign``

![](https://i.gyazo.com/31360a6fe0eb3fb7805ed6e9e7734de8.png)

Je transmets ces fichiers et Emma va vérifier la signature.

Avec sa clé publique, qui n'est pas la bonne pour ce fichier :

![](https://i.gyazo.com/39ee28e66d8e3bc41a58de0a16c7e93a.png)

Avec la bonne clé publique :

![](https://i.gyazo.com/3dd6000cf1aa4e0a50e8b9ea1cbfbbd1.png)
