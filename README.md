# Visualiseur des données de la CoopTech

Widget **[Datami](https://gitlab.com/multi-coop/datami)** de prévisualisation des données de la CoopTech.

---

## Résumé

La CoppTech cherche à constituer un annuaire le plus complet possible des SCOP et autres coopératives du numérique en France. Cet annuaire prend la forme d'un simple fichier `.csv` hébergé sur un repo [Github](https://github.com/multi-coop/gitribute-content-test/blob/main/data/csv/cooptech/Annuaire-SCOP-SCIC-tech-France.csv) ou [Gitlab](https://gitlab.com/multi-coop/gitribute-content-test/-/blob/main/data/csv/cooptech/Annuaire-SCOP-SCIC-tech-France.csv)

Afin de pouvoir partager et de mettre en valeur toutes ces ressources il a été proposé d'utiliser le _widget open source_ créé par la coopérative numérique **[multi](https://multi.coop)** : le projet **[Datami](https://gitlab.com/multi-coop/datami)**.

Cet outil permet la **visualisation** des données mais également la **contribution**.

**Datami** permet d'intégrer sur des sites tiers (sites de partenaires ou autres) une sélection plus ou moins large de ressources. Cette solution permet à la fois d'éviter aux sites partenaires de "copier-coller" les ressources, d'afficher sur ces sites tiers les ressources toujours à jour, et de permettre aux sites tiers ainsi qu'au site source de gagner en visibilité, en légitimité et en qualité d'information.

L'autre avantage de cette solution est qu'elle n'est déployée qu'une fois, mais que le widget peut être intégré et paramétré/personnalisé sur autant de sites tiers que l'on souhaite... **gratuitement**.

---

## Démo

[![Netlify Status](https://api.netlify.com/api/v1/badges/57d96b44-b6c4-4f0a-a7f7-412571f23aa2/deploy-status)](https://app.netlify.com/sites/datami-demo-cooptech/deploys)
- URL de démo : 
  - DEMO / données CoopTech : https://datami-demo-cooptech.netlify.app/

---

### Documentation 

Un site dédié à la doucmentation technique de Datami est consultable ici : https://datami-docs.multi.coop


---

## Mini server for local development

A mini server is writen in the `server.py` to serve this folder's files, so we could test and develop locally while running [multi-site-app]()

To install the mini-server :

```sh
pip install --upgrade pip
python3 -m pip install --user virtualenv
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

or

```sh
sh setup.sh
source venv/bin/activate
```

---

### Geocoder

To geocode the dataset :

```sh
python geocoder.py csv/rhinocc-inclusion-dataset.csv -sep , -adress Adresse
```

or

```sh
sh run_geocoding.sh
```

The output geocoded file will be generated at `csv/geocoding/geocoded.csv`

---

### Run local server

To run the server on `http://localhost:8801`:

```sh
python server.py
```

or

```sh
sh run_server.sh
```

Files will be locally served on :

- `http://localhost:8801/content/<path:folder_path>/<string:filename>`
- `http://localhost:8801/statics/<path:folder_path>/<string:filename>`

---

## Crédits

| | logo | url |
| :-: | :-: | :-: |
| **CoopTech** | ![ODF](./images/cooptech_logo.svg) | https://www.cooptech.fr/ |
| **coopérative numérique multi** | ![multi](./images/multi-logo.png) | https://multi.coop |

---

## Pour aller plus loin...

### Datami

Le widget fait partie intégrante du projet [Datami](https://gitlab.com/multi-coop/datami)
