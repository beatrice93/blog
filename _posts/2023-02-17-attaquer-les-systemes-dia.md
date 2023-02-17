---
layout: post
title: Attaquer un système d'IA
categories:
    - "vulgarisation"
    - "notes"
    - "french"
tags:
    - "french"
---

Quelques notes personnelles sur l'article de la CNIL intitulé "Petite taxonomie des attaques des systèmes d'IA (disponible [ici](https://linc.cnil.fr/fr/petite-taxonomie-des-attaques-des-systemes-dia)).

<!--more-->

## Les types d'attaques

On distingue trois grands types d'attaques des systèmes d'IA

- **Manipulation.** Ces attaques visent à modifier le comportement du système pour en dégrader les performances, voire lui faire effectuer des tâches pour lesquelles il n'a pas été entraîné. C'est dans cette catégorie qu'on retrouve notamment toutes les attaques à base d'exemples contradictoires (adversaires).
- **Infection.** Ces attaques visent à scrètement influencer les performances du système d'IA en utilisant en particulier des données manipulées pendant la phase d'entraînement. Elles sont en général perpétrées par les personnes distribuant le modèle, mais aussi par ses utilisateurs dans le cas de l'apprentissage continu.
- **Exfiltration.** Ces attaques ont pour but d'extraire des informations sur le système, par exemple, les données qui ont été utilisées pour l'entraîner, les paramètres, le type de modèle, etc.

## Manipulation

Ces attaques ont principalement lieu en phase de production : on part donc du principe qu'on n'a pas accès aux données. Il en existe trois types : évasion, reprogrammation, déni de service.

### L'évasion

Il s'agit de présenter au modèle des observations pour lesquelles ses performances sont dégradées ; en général, celles-ci sont constituées d'une observation "normale" (par exemple, une photo), à laquelle on va ajouter du bruit (une superposition de pixel, un patch, un sticker, etc.) afin de perturber les capacités du modèle. On citera le fameux exemple du panda-gibbon ou celui, plus effrayant, du panneau stop se transformant en limite de vitesse par l'ajout d'un sticker.

![un panda avec la légende "panda", un carré contenant du bruit, et la même image de panda avec la légende "gibbon"](https://wp.technologyreview.com/wp-content/uploads/2019/05/adversarial-10.jpg)

### La reprogrammation

Cette technique nécessite d'avoir accès aux données, ou de pouvoir injecter de nouvelles données dans le modèle pendant un entraînement continu. Elle consiste en l'utilisation de nouvelles données permettant de détourner la finalité du modèle : par exemple, un modèle de reconnaissance d'animaux peut être entraîné à compter les points dans une image, et à renvoyer le nom d'un animal en fonction de ceux-ci (par exemple, "chien" pour 1 point, "chat" pour 2 points etc). On peut imaginer bien sûr des attaques plus sophistiquées, où un modèle serait reprogrammé pour miner de la cryptomonnaie ou pour résoudre des captchas en ligne. 

Note : Le mot "attaque" fait percevoir une réalité en noir et blanc, avec les gentils concepteurs des modèles d'IA d'un côté, et les vilains utilisateurs de l'autre ; dans le cas de la reprogrammation, l'attaque peut venir d'un concepteur mal intentionné.

### Le déni de service

Comme pour un site web, l'idée ici est de surcharger un modèle en lui envoyant des requêtes spécifiquement élaborées pour être extrêmement gourmandes en énergie, et susciter la mise hors ligne du système.

## Infection

Ces attaques ont toutes lieu en phase d'entraînement, puisqu'il s'agit de modifier les données.

### L'empoisonnement

Il s'agit ici de modifier la distribution des données en entrée (en éliminant, ajoutant, ou perturbant des observations) pour altérer le comportement du modèle en sortie. Contrairement aux exemples contradictoires, qui consistent à changer une donnée que l'on soumet au système pour prédiction, l'attaquant va ici changer les données du jeu d'entraînement afin de déplacer la frontière de décision du modèle (exemple : si on ne garde dans un jeu de données que les chats noirs et les chiens blancs, un classifieur risque de confondre un chien noir avec un chat).

### La porte dérobée

On va secrètement modifier directement le système afin que certaines requêtes donnent un résultat particulier : par exemple, on s'arrange pour que le modèle reconnaisse systématiquement une image comme étant celle d'un dauphin si un carré blanc est présent en haut à gauche.

## Exfiltration

Ces attaques ont toujours lieu en phase de production, c'est-à-dire a posteriori. On va chercher à réupérer des information sur le modèle d'IA. Ce sont celles qui m'intéressent le plus, en tant que féru de confidentialité et de numérique responsable. Nous les retrouverons dans une prochaine série de posts sur ce blog, je les décris donc assez brièvement.

### L'inférence d'appartenance (membership inference)

On cherche à savoir si une observation (ou un groupe d'observations) ont été utilisées comme données d'entraînement. En pratique, on va se baser sur les performances du modèle, qui sont toujours meilleures sur les exemples utilisés pour l'entraînement que sur les autres.


### L'inversion de modèle

On va chercher ici à reconstituer des données d'entrées à partir de requêtes envoyées au système. C'est donc une attaque plus détaillée et plus puissante que l'inférence d'appartenance, qui suppose qu'on a déjà les données et qu'on veut simplement vérifier leur présence dans le jeu d'entraînement.

### L'extraction de modèle

Comme son nom l'indique, cette attaque vise à voler le modèle (ou certains de ces paramètres) en le reconstituant à partir de ses réponses à de multiples requêtes. 

## Conclusion

Merci à la CNIL pour cette taxonomie fort utile. Dans un futur post, je m'intéresserai en particulier aux attaques de type exfiltration, et des manières de s'en prémunir.
