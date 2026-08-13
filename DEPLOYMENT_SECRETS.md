# Secrets GitHub - Config Repo

Ces secrets doivent etre crees dans le repository GitHub du config repo.

## Acces VPS

- `VPS_HOST` : adresse IP ou domaine du VPS.
- `VPS_USER` : utilisateur SSH de deploiement.
- `VPS_SSH_PORT` : port SSH, souvent `22`.
- `VPS_SSH_PRIVATE_KEY` : cle privee SSH autorisee sur le VPS.
- `VPS_APP_DIR` : repertoire applicatif sur le VPS, par exemple `/opt/target4c2`.

## Principe

Un push ou merge sur `main` du repo de configuration redemarre `config-service`, puis les services qui consomment cette configuration.
Les branches `dev` et `develop` ne declenchent aucun deploiement.
