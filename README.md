## Deployement du Redis

    Le fichier moindjie_redis.yaml lance le déploiement du pod redis.
    L'exposition du pod vers l'extérieur se fait par le bias du fichier
    "moindjie_service_redis.yaml" pour permettre cette connexion et
    la création de cette service.

## Deployement de node-redis

    On fait un déploiement des pods node-redis à l'aide du fichier
    "moindjie_serveur.yaml" en précisant la clé "kind" :Deployment
    A la suite, on crée un service en s'appuyant du ficher
    "moindjie_service_redis.yaml". On peut donc augmenter le nombre
    réplicas.
    La connexion du service node-redis au service redis se fait par le
    biais de "imagePullSecrets" et le varibale d'environement

##

    spec :
      imagePullSecrets:
        - name: regcred

##

    env:
      - name: REDIS_URL
          value: "redis://10.3.147.76:6379"
