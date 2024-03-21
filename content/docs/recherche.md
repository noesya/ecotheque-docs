---
title: Recherche
---

On utilise ElasticSearch pour la recherche.

## Installation

*NOTE : On ne peut pas utiliser Homebrew pour installer ElasticSearch car la formule actuelle (au 21 mars 2024) ne fonctionne pas sur les dernières versions de macOS.*

*NOTE 2 : On utilise la version 7 d'ElasticSearch car Scalingo ne supporte pas la version 8 (au 21 mars 2024).*

Télécharger et décompresser ElasticSearch.

```bash
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.18-darwin-x86_64.tar.gz
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.18-darwin-x86_64.tar.gz.sha512
shasum -a 512 -c elasticsearch-7.17.18-darwin-x86_64.tar.gz.sha512
tar -xzf elasticsearch-7.17.18-darwin-x86_64.tar.gz
```

Déplacer le dossier dans `/usr/local`.

```bash
sudo mv elasticsearch-7.17.18 /usr/local
```

Modifier votre fichier `.zshrc` avec `nano ~/.zshrc` et ajouter les lignes suivantes.

```bash
export ES_HOME=/usr/local/elasticsearch-7.17.18
export PATH=$ES_HOME/bin:$PATH
```

Pour appliquer les modifications, relancer un Terminal ou exécuter `source ~/.zshrc`.

Démarrer ElasticSearch.

```bash
elasticsearch
```

Couper ElasticSearch en faisant Ctrl+C et modifier le fichier de configuration avec `nano $ES_HOME/config/elasticsearch.yml`, et modifier la ligne suivante.

```yml
xpack.security.enabled: false # Le passer de "true" à "false"
```

Puis relancer ElasticSearch.

## Utilisation

Pour lancer le processus ElasticSearch, il suffit d'exécuter `elasticsearch` dans le Terminal. Pour l'arrêter, il suffit de faire Ctrl+C.

Pour lancer ElasticSearch en arrière-plan, exécuter `elasticsearch -d -p $ES_HOME/pid`. Pour l'arrêter, exécuter `pkill -F $ES_HOME/pid`.

## Réindexer les modèles recherchables

```bash
rails app:search:reindex
```
