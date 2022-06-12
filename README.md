# Visualiseur des données de l'Observatoire de l'Open Data

Widget de prévisualisation des données issues de fichiers csv de l'Observatoire de l'Open Data - Open Data France.

---

## Résumé

Open Data France possède un site (https://www.observatoire-opendata.fr/) visant à mesurer le déploiement de l'open data en France, à sensibiliser les collectivitées et les acteurs publics à l'open data, et à valoriser ces données sous formes de diverses visualisations . Sont référencés sur ce site différents types de données : organisations, plateformes, etc...

Afin de pouvoir partager et de mettre en valeur toutes les ressources de ce wiki il a été proposé de créer un outil numérique de type "widget" : `gitribute-file`. En effet un outil de ce type permet de pouvoir intégrer sur des sites tiers (sites de partenaires ou autres) une sélection plus ou moins large de ressources. Cette solution permet à la fois d'éviter aux sites partenaires de "copier-coller" les ressources, d'afficher sur ces sites tiers les ressources toujours à jour, et de permettre aux sites tiers ainsi qu'au site source de gagner en visibilité, en légitimité et en qualité d'information.

L'autre avantage de cette solution est qu'elle n'est déployée qu'une fois, mais que le widget peut être intégré et paramétré/personnalisé sur autant de sites tiers que l'on souhaite... gratuitement.

La solution proposée et réalisée ici s'appuie sur un projet open source porté par la coopérative numérique [**multi**](https://multi.coop) : le projet [Gitribute](#gitribute-).

A titre de démonstration de généricité de cette solution de widget nous l'avons déclinée de différentes manières, par exemple en configurant et intégrant ce widget pour qu'il affiche des "communs" référencés sur le wiki [Résilience des territoires](https://wiki.resilience-territoire.ademe.fr).

---

## Démo

- Déploiement du code source de l'applicatif (gitribute) : [![Netlify Status](https://api.netlify.com/api/v1/badges/693b562e-5ff8-4101-9cdb-157f7be2d3d2/deploy-status)](https://app.netlify.com/sites/multi-gitribute-test/deploys)
- Page html de démo : [![Netlify Status](https://api.netlify.com/api/v1/badges/854fd222-efeb-4f27-a879-0484bcd8af69/deploy-status)](https://app.netlify.com/sites/demo-odf-data-observatoire/deploys)
- url de démo : 
  - gitribute-file / données observatoire ODF : https://demo-odf-data-observatoire.netlify.app/

---

## Captures d'écran

... en construction ...

---

### Sommaire

- [Résumé](#resume-)
- [Intégration du widget](#integration-du-widget-)
- [Configuration du widget](#configuration-du-widget-)
<!-- - [Paramètres et options](#parametres-et-options-)
  - [paramètre `wikilist`](#parametre-wikilist-)
  - [paramètre `wikipages`](#parametre-wikipages-)
  - [paramètre `title`](#parametre-title-)
  - [paramètre `options`](#parametre-options-)
  - [paramètre `locale`](#parametre-locale-)
  - [paramètre `onlypreview`](#parametre-onlypreview-)
  - [paramètre `debug`](#parametre-debug-) -->
- [Crédits](#credits-)
- [Gitribute](#gitribute-)
- [Stack](#stack-)
- [Pour aller plus loin...](#pour-aller-plus-loin-)

---

### Intégration du widget [⇡](#sommaire)

Le widget nécessite d'importer deux fichiers dans votre page html (de préférence dans la balise `head`) :

- `app.js`
- `app.css`

Ces deux fichiers sont hébergés à l'adresse `https://multi-gitribute-test.netlify.app`, il est donc possible de les importer de la manière suivante :

```html
<script src="https://multi-gitribute-test.netlify.app/js/app.js" type="text/javascript"></script>

<link type="text/css" href="ttps://multi-gitribute-test.netlify.app/css/app.css" rel="stylesheet">
```

Le widget peut alors être utilisé et configuré/personnalisé directement dans la partie `<body>` de la page html. 

### Configuration du widget [⇡](#sommaire)

Le tag à utiliser pour intégrer le widget est : `<multi-gitribute-file/>`

Le widget permet de récupérer et afficher sous forme de tuiles (cartes) un ensemble de ressources présentes dans un fichier csv.

Le widget peut être configuré en paramétrant différentes options :

```html
  <!-- Exemple d'une intégration permettant de charger des ressources wiki distantes -->
  <multi-gitribute-file 
    wikilist="https://github.com/multi-coop/gitribute-content-test/blob/main/data/csv/odf/ODF-Observatoire-apiviz_data-export_solidata-220425b-simplified.csv"
    options='{<YOUR-OPTIONS>}'
    title="gitribute for my file :)"
    usertoken="MY-USER-TOKEN or GHOST-USER-TOKEN"
    locale="fr"
  ></multi-gitribute-file>
```

```html
  <!-- Exemple d'une intégration permettant de charger des ressources csv distantes -->
    <multi-gitribute-file
      gitfile="https://github.com/multi-coop/gitribute-content-test/blob/main/data/csv/odf/ODF-Observatoire-apiviz_data-export_solidata-220425b-simplified.csv"
      options='{
      "separator":";",
      "lockcolumns": true,
      "tagseparator":"-",
      "height": "800px",
      "pagination":{
        "itemsPerPage":30
      },
      "cardsview": { "activate": true, "default": false },
      "cardsdetail": true,
      "cardssettings": {
        "mini": {
          "nom": {"position": "title"},
          "siren": {"position": "resume"},
          "tags": {"position": "tags"}
        },
        "detail": {
          "nom": {"position": "title"},
          "orga": {"position": "resume"},
          "siren": {"position": "description"},
          "adress": {"position": "description"},
          "dep_label": {"position": "tags"},
          "tags": {"position": "tags"}
        }
      }
    }' title="gitribute for ODF github file - csv ( semicolon separator)"
      usertoken="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" locale="fr" debug="false">
    </multi-gitribute-file>
```

---

## Crédits [⇡](#sommaire)

| | logo | url |
| :-: | :-: | :-: |
| **Open Data France** | ![ODF](./images/odf-logo.svg) | https://www.opendatafrance.net/ |
| **coopérative numérique multi** | ![multi](./images/multi-logo.png) | https://multi.coop |

---

## Pour aller plus loin...  [⇡](#sommaire)

### Gitribute [⇡](#sommaire)

Le widget fait partie intégrante du projet [Gitribute](https://gitlab.com/multi-coop/gitribute)

### Stack technique [⇡](#sommaire)

We only used open source packages and technologies, coz' that's what we do... :

- [`Vue.js` (2.x)](https://v2.vuejs.org/v2/guide) : yes we like this framework a lot...
- [`VueX`](https://vuex.vuejs.org/): the data store shared for every web component ;
- [`vue-custom-element`](https://github.com/karol-f/vue-custom-element): wrapper for vue web components ;
- [`gray-matter`](https://www.npmjs.com/package/gray-matter): package to convert `md` or `yaml` content to object ;
- [`Showdown`](https://www.npmjs.com/package/showdown) and [`showdown-table` extension](https://github.com/showdownjs/table-extension#readme): package to convert `md` content to `html` (see [docs for showdown extensions](https://github.com/showdownjs/showdown#extensions));
- [`Bulma`](https://bulma.io/) and [`Buefy`](https://buefy.org/) : as UI frameworks for vue ;
- [`Material Design`](https://materialdesignicons.com/) fonts: for icons ;
- [`Fetch`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch): for requests to Github's or Gitlab's API ;
- [`JSDiff`](https://github.com/kpdecker/jsdiff) : to get diff between an original content and its edited version
- [`Diff2html`](https://www.npmjs.com/package/diff2html) : to display diff like in github / gitlab
- ...and a lot of Stackoverflow help...
