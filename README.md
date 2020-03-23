# Bib Gourmand

## Introduction

Voici mon projet, celui a été réalisé avec Angular 8 et node.js

Avant de continuer je vous invite à le visiter : 

https://bibgourmand-front-6yr4ksia6a-ew.a.run.app

## Récupérer des données de 2 sources différentes pour créer une web app

A l'aide de node.js et des librairies Axios et Cheerio, je récupère la liste des restaurants depuis les site web du guide Michelin (michelin-scraper.js) et des Maitres-Restaurateurs (maitre-scraper.js) .

C'est deux script créer deux JSON, correspondant chacun à un site web, ceux-ci sont différents.

**Michelin** : 

```
{
  "title": "Le Lancelot",
  "type": "Cuisine moderne",
  "location": "Chilleurs-aux-Bois",
  "link": "https://guide.michelin.com/fr/fr/centre-val-de-loire/chilleurs-aux-bois/restaurant/le-lancelot",
  "image": "https://d3h1lg3ksw6i6b.cloudfront.net/guide/fr/2020/xlarge/2173_pro_6.jpg"
}
```

**Maitre** : 

```
{
  "name": "LE TEMPS D'M",
  "address": "3 rue Ferdinand Dubouloz74200 THONON-LES-BAINS",
  "tel": "0450725358"
}
```

On peut voir que les mêmes donnés ne sont pas présentes dans les deux json.

Une fois les donnés récupérer, j'ai créer une API qui s'occupe de les distribuer au front end de mon application.

C'est dans celle-ci que le regroupement des donnés se fait, je regarde pour le même nom de Restaurant et j'envoie le Restaurant complet si celui-ci répond bien à nos critères.

Voici le JSON associé : 

```
{
    "name": "Le Lancelot",
    "city": "Chilleurs-aux-Bois",
    "link": "https://guide.michelin.com/fr/fr/centre-val-de-loire/chilleurs-aux-bois/restaurant/le-lancelot",
    "type": "Cuisine moderne",
    "picturelink": "https://d3h1lg3ksw6i6b.cloudfront.net/guide/fr/2020/xlarge/2173_pro_6.jpg",
    "adress": "12 rue des Deportes45170 CHILLEURS-AUX-BOIS",
    "phone": "0238329115"
}
```

Afin de réaliser mon API, j'utilise express ainsi que Postman afin de tester celle-ci.

J'ai également réaliser un endpoint pour la recherche de restaurant plutôt que de le faire dans le front end.


## Le front End de l'application

Celui-ci a été réalisé à l'aide d'Angular 8 ainsi que Bootstrap pour le html et le css.


Il y a 2 parties pour la page web :

![Le jumbotron](/files/jumbotron.png)

Il y a la barre de recherche, ainsi qu'un bouton afin de filtrer par ordre Alphabétique, je n'ai pas réalisé le filtrage par distance.

![Cards](/files/cards.png)

Et ensuite voilà ma liste d'élement. Chaque élément propose un lien vers la page du guide michelin, mais permet aussi l'ouverture de google maps directement dans l'application.

![Card](/files/card.png)

Concernant le code, la plupart du travail est dans le html et dans la réalisation du service pour communiquer avec l'API.

## Upload du site sur internet

Afin de l'upload sur internet je suis passer par la plateforme Google Cloud.

J'ai réalisé 2 images docker, une pour le backend et une autre pour le front.

J'ai ensuite upload ces deux images sur Google Cloud et voilà le site est online ! 