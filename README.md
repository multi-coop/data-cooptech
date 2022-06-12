# Visualiseur des données de la CoopTech

Widget de prévisualisation des données de la CoopTech.

---

## Résumé

La CoppTech cherche à constituer un annuaire le plus complet possible des SCOP et autres coopératives du numérique en France. Cet annuaire prend la forme d'un simple fichier `.csv` hébergé sur un repo [Github](https://github.com/multi-coop/gitribute-content-test/blob/main/data/csv/cooptech/Annuaire-SCOP-SCIC-tech-France.csv) ou [Gitlab](https://gitlab.com/multi-coop/gitribute-content-test/-/blob/main/data/csv/cooptech/Annuaire-SCOP-SCIC-tech-France.csv)

Afin de pouvoir partager et de mettre en valeur toutes les ressources de la CoopTech il a été proposé d'utiliser le _widget open source_ créé par la coopérative numérique [**multi**](https://multi.coop) : le projet **[Gitribute](https://gitlab.com/multi-coop/gitribute)**.

Cet outil permet la **visualisation** des données mais également la **contribution**.

**Gitribute** permet d'intégrer sur des sites tiers (sites de partenaires ou autres) une sélection plus ou moins large de ressources. Cette solution permet à la fois d'éviter aux sites partenaires de "copier-coller" les ressources, d'afficher sur ces sites tiers les ressources toujours à jour, et de permettre aux sites tiers ainsi qu'au site source de gagner en visibilité, en légitimité et en qualité d'information.

L'autre avantage de cette solution est qu'elle n'est déployée qu'une fois, mais que le widget peut être intégré et paramétré/personnalisé sur autant de sites tiers que l'on souhaite... **gratuitement**.

---

## Démo

- Déploiement du code source de l'applicatif (gitribute) : [![Netlify Status](https://api.netlify.com/api/v1/badges/693b562e-5ff8-4101-9cdb-157f7be2d3d2/deploy-status)](https://app.netlify.com/sites/multi-gitribute-test/deploys)
- Page html de démo : [![Netlify Status](https://api.netlify.com/api/v1/badges/57d96b44-b6c4-4f0a-a7f7-412571f23aa2/deploy-status)](https://app.netlify.com/sites/demo-gitribute-cooptech/deploys)
- url de démo : 
  - gitribute-file / données CoopTech : https://demo-gitribute-cooptech.netlify.app/

---

## Captures d'écran

`... en construction ...`

---

### Sommaire

- [Résumé](#resume-)
- [Intégration du widget](#integration-du-widget-)
- [Crédits](#credits-)
- [Pour aller plus loin...](#pour-aller-plus-loin-)
  - [Gitribute](#gitribute-)
  - [Stack](#stack-)

---

### Intégration du widget [⇡](#sommaire)

Le widget nécessite d'importer deux fichiers dans votre page html (de préférence dans la balise `<head>`) :

- `app.js`
- `app.css`

Ces deux fichiers sont hébergés à l'adresse `https://deploy-preview-7--multi-gitribute.netlify.app`, il est donc possible de les importer dans la balise `<head>` de votre page html. Le widget peut alors être utilisé et configuré/personnalisé directement dans la partie `<body>` de la page html.

```html
<!-- IMPORT DE L'APPLICATIF DU WIDGET (DANS LA BALISE <head>) -->
<script src="https://deploy-preview-7--multi-gitribute.netlify.app/js/app.js" type="text/javascript"></script>
<link type="text/css" href="https://deploy-preview-7--multi-gitribute.netlify.app/css/app.css" rel="stylesheet">

<!-- INTEGRATION DU WIDGET POUR LES DONNEES SOUHAITEES (DANS LA BALISE <body>) -->
<multi-gitribute-file
  gitfile="https://github.com/multi-coop/gitribute-content-test/blob/main/data/csv/cooptech/Annuaire-SCOP-SCIC-tech-France.csv"
  options='{
    "height": "500px",
    "separator":",",
    "lockcolumns": true,
    "tagseparator":",",
    "customfilters" : {
      "activate": true,
      "filterfields": [
      "type",
        "Statut juridique"
        ]
    },
    "schema": {
      "file": "https://github.com/multi-coop/gitribute-content-test/blob/main/data/json/cooptech/Annuaire-SCOP-SCIC-tech-France-schema.json"
    },
    "fields-custom-properties": {
      "file": "https://github.com/multi-coop/gitribute-content-test/blob/main/data/json/cooptech/Annuaire-SCOP-SCIC-tech-France-fields-custom-props.json"
    },
    "customsorting" : {
      "activate": true,
      "sortfields": [
        { "name": "Nom" }
      ]
    },
    "pagination":{
      "itemsPerPage": 20
    },
    "cardsview": { "activate": true, "default": false },
    "cardsdetail": true,
    "cardssettings": {
      "mini": {
        "Nom": {"position": "title"},
        "Présentation": {"position": "description"},
        "Site internet": {"position": "description"},
        "Statut juridique": {"position": "tags"},
        "Domaine(s)": {"position": "tags"}
      },
      "detail": {
        "Nom": {"position": "title"},
        "Site internet": {"position": "description"},
        "Présentation": {"position": "description"},
        "Numéro SIREN": {"position": "description"},
        "Adresse": {"position": "description"},
        "Statut juridique": {"position": "tags"},
        "Domaine(s)": {"position": "tags"},
        "Fiche URSCOP": {"position": "links"}
      }
    }
  }'
  title="Liste des coopératives de la tech en France - csv ( semicolon separator)"
  usertoken=""
  locale="fr"
  debug="false"
/>

```


---

## Crédits [⇡](#sommaire)

| | logo | url |
| :-: | :-: | :-: |
| **CoopTech** | ![ODF](./images/cooptech_logo.svg) | https://www.cooptech.fr/ |
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
