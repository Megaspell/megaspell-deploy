# megaspell-deploy
Deployment infrastructure based on docker-compose because we don't need anything fancier yet.
Any change to this repo will be instantly deployed.  

### Repository setup
1. Configure secrets:
    - `GHCR_USER` is the GitHub user OR organization that will be accessing GitHub package registry.
    - `GHCR_READ_TOKEN` should be a token with `read:packages` permission. As of *2023-11-24* fine-grained tokens can't be used for that.
    - `POSTGRES_MASTER_PASSWORD` is password of `postgres` user and `POSTGRES_MEGASPELL_PASSWORD` is password for `megaspell` user.
    - `GRAFANA_GITHUB_APP_CLIENT_ID` and `GRAFANA_GITHUB_APP_SECRET` - creds GitHub app that will be used for authentication in Grafana.
### Server setup
1. Configure secrets:
    - `DEPLOY_HOST` and `DEPLOY_PORT` - SSH host:port of target server. Port is optional.
    - `DEPLOY_USER` - SSH user.
    - Either `DEPLOY_PASSWORD` or `DEPLOY_KEY` for SSH access.
2. Install required software if not installed:
   - Docker Engine: https://docs.docker.com/engine/install/
3. Allow deploy user to use Docker: `sudo groupadd $DEPLOY_USER && sudo usermod -aG docker $DEPLOY_USER`
4. Add GitHub key to known hosts: `ssh github.com`