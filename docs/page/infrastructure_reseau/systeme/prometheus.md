![Prometheus](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Prometheus_software_logo.svg/2066px-Prometheus_software_logo.svg.png){ align=right width="200" }

Prometheus est un outil de surveillance et d’alerte open source qui a été créé par SoundCloud en 20121. Il est conçu pour surveiller les métriques de fonctionnement des serveurs et créer une gestion d’alertes en fonction de seuils considérés critiques. 

Il est principalement un agrégateur de métriques qui collecte des données en série temporelle auprès de cibles configurées, qu’elles soient des applications, des services ou des dispositifs informatiques. Les métriques sont collectées à partir de cibles comme des points de terminaison (ou endpoints). Ces cibles (targets) peuvent s’agir d’applications, de services, de serveurs, de conteneurs, de bases de données qui exposent des métriques via un point de terminaison HTTP spécifique appelé « endpoint de collecte des métriques » (metrics endpoint).

Prometheus utilise une architecture décentralisée pour être fiable même dans les circonstances adverses. Il est souvent utilisé dans une configuration distribuée pour augmenter la disponibilité et la redondance.

Grâce à son intégration facile avec Kubernetes et à son écosystème riche, Prometheus est devenu un élément essentiel du suivi dans les environnements DevOps. - Copilote

### Installation - Docker
On va donc ici utiliser docker pour installer Prometheus, pour cela on va utiliser la commande suivante : 
```bash
docker run -p 9090:9090 prom/prometheus
```

Une fois l'installation fini, vous pouvez accéder a l'interface de Prometheus avec l'adresse `localhost:9090` et vous pouvez commencer a utiliser l'outil.

### Installation - Windows_exporter
Pour sa on va utiliser [windows_exporter](https://github.com/prometheus-community/windows_exporter) pour récupérer les donnée des client windows. Vous avez donc besoin de télécharger le fichier qui correspond a votre besoin.

!!! info "Information"
    on choisie ce logicile car on veux récupérer les données par la suivte avec [Grafana](#grafana) en passant par Prometheus.

Une fois le fichier télécharger, vous l'instaler, uen page terminal va s'ouvvrir et on va vous demander si vous voulais donner les autorisation. Une fois fini utiliser l'adresse `localhost:9182` pour avoir les informations, récupérer.

### Utilisation
On va donc devor ajouter notre machine a la configuration de Prometheus pour récupérer les données. On va donc modifier le fichier `prometheus.yml` (dans mon cas il etait a `/etc/prometheus/prometheus.yml`) pour ajouter notre machine. 
```yml
- job_name: 'win-exporter'
    static_configs:
      - targets: ['<adresse ip du client>:9182']
```
Une fois la configuration faite, on va redémarrer le service pour que les changements soit pris en compte. *Vous pouvez verfifiez que la configuration a bien était prise en compte en allans sur Prometheus->Status->Targets et verifier que le client est bien présent et connecté*.

On va passer a la configuration de [Grafana](#grafana) pour récupérer les données et pouvoir les exploiter dessus.