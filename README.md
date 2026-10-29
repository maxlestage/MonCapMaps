# MonCapMaps

Les paquets hors ligne de l'app **MonCap GPS** : une Release par région,
avec ses fichiers.

| Fichier | Contenu |
| --- | --- |
| `<région>.tar` | les tuiles Valhalla (calcul d'itinéraire sur l'appareil) |
| `<région>.json` | la configuration Valhalla qui les accompagne |
| `<région>.lieux.zz` | l'annuaire des lieux (recherche hors réseau) |
| `<région>.rues.zz` | l'index des voies nommées |
| `<région>.vitesses.zz` | les jalons de limites de vitesse |

Le dépôt est **public** et ne contient que cela : l'app lit la liste sur
l'API GitHub et télécharge les fichiers sans jeton ni serveur, alors que le
code de l'app reste privé dans `maxlestage/moncap`.

## Workflows

- **Tuiles Valhalla** (`valhalla-tiles.yml`, manuel) : construit et publie
  des régions depuis les extraits Geofabrik (`france,portugal`, `europe`,
  `grandes-regions`).
- **Épreuve Valhalla** (`valhalla-epreuve.yml`, chaque lundi) : Bordeaux →
  Limoges sur le paquet publié, Toulouse en contrôle négatif.
- **Ménage Valhalla** (`valhalla-menage.yml`, manuel) : retire les Releases
  qui ne correspondent plus au découpage.
- **Copie depuis moncap** (`copie-depuis-moncap.yml`, manuel, une fois) :
  recopie les régions publiées jusqu’ici sur `maxlestage/moncap` (privé :
  secret `MONCAP_TOKEN`, « Contents: read »), en
  gardant leur date de construction (ligne `construit: …` des notes).

Données © OpenStreetMap contributors, sous licence ODbL.
