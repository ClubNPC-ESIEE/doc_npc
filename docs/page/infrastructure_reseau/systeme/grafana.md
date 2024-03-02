![Grafana](https://cdn.icon-icons.com/icons2/2699/PNG/512/grafana_logo_icon_171048.png){ align=right width="200" }

Grafana est une plateforme open source pour la visualisation et l'analyse de données. Elle est utilisée pour créer des graphiques, des diagrammes et d'autres représentations de données provenant de diverses sources. Ces sources peuvent être des bases de données, des services en nuage ou des applications en réseau.

Grafana permet d'obtenir des métriques qui donnent un sens à d'énormes quantités de données et de surveiller vos applications à l'aide de tableaux de bord personnalisables. Il vous permet également d'écrire des plugins à partir de zéro pour l'intégration avec plusieurs sources de données différentes.

Grafana se connecte à toutes les sources de données possibles, communément appelées bases de données telles que Prometheus, ElasticSearch, MySQL, PostgreSQL, Graphite, Influx DB et OpenTSDB. L'outil vous aide à étudier, analyser et surveiller les données sur une période de temps, ce qui est techniquement appelé analyse de séries chronologiques.

Il vous permet de suivre le comportement des utilisateurs, le comportement de l'application, la fréquence des erreurs qui apparaissent dans un environnement de production ou de pré-prod, le type d'erreurs qui apparaissent et les scénarios contextuels en fournissant des données relatives.

L'un des grands avantages de Grafana est qu'il peut être déployé sur site. C'est avantageux pour les organisations qui ne souhaitent pas que leurs données soient transmises à un fournisseur de cloud computing pour des raisons de sécurité et autres.

En résumé, Grafana fonctionne en intégrant des sources de données, en les affichant à l'aide de graphiques et de tableaux et en signalant les anomalies à l'aide d'alertes. Il aide à comprendre les données de manière rapide et efficace pour prendre des décisions adaptées à la situation. - Copliote

### Installation - Docker
On va ici choisir une installation docker de Grafana, pour cela on va utiliser le tutoriel d'installation de base proposer par Grafana.

On va donc utiliser la commande : 
```bash
docker run -d --name=grafana -p 3000:3000 grafana/grafana-enterprise
```

Une fois l'installation fini, vous pouvez accéder a l'interface de Grafana avec l'adresse `localhost:3000` et vous connecter avec les identifiants par défaut `admin:admin`, il vous sera demander de changer le mot de passe.

### Utilisation

#### Configuration avec [Prometheus](#prometheus)

#### Création de Dashboard
On va dans notre cas importer le dashboard `14510`, pour avoir tout se qui nous faut.

[^]: [autre tutoriel](https://www.fosstechnix.com/install-prometheus-and-grafana-with-wmi-exporter-on-window-server-2022-base/) - https://www.fosstechnix.com/install-prometheus-and-grafana-with-wmi-exporter-on-window-server-2022-base/