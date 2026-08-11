# Target4C2 Config Repository

Ce repertoire est le depot Git attendu par `config-service` pour distribuer la configuration YAML des microservices Target4C2.

## Structure

- `application.yml` : configuration commune a tous les services.
- `application-local.yml` : valeurs communes pour le developpement local.
- `application-dev.yml` : valeurs communes pour l'environnement de recette/dev distant.
- `application-prod.yml` : garde-fous et placeholders de production.
- `<service-name>.yml` : configuration propre a chaque microservice.

## Services couverts

- `config-service`
- `discovery-service`
- `api-gateway`
- `identity-access-service`
- `public-cms-marketing-service`
- `learning-content-service`
- `training-pedagogy-service`
- `commerce-operation-service`

## Connexion GitHub

1. Creer un depot GitHub prive, par exemple `target4c2-config-repo`.
2. Pousser ce repertoire comme racine du depot.
3. Definir dans le `config-service` :

```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: ${CONFIG_GIT_URI:https://github.com/ORG/target4c2-config-repo.git}
          username: ${CONFIG_GIT_USERNAME:}
          password: ${CONFIG_GIT_TOKEN:}
          default-label: ${CONFIG_GIT_BRANCH:main}
```

## Regles

- Ne jamais committer de secrets reels.
- Utiliser les variables d'environnement pour les mots de passe, tokens, cles Stripe, SMTP, JWT et AWS.
- Modifier les ports uniquement si l'orchestration locale ou cloud est mise a jour en meme temps.
- Toute nouvelle configuration doit rester compatible avec les profils `local`, `dev` et `prod`.
