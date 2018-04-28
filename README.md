# nywater.info
Production deployment and documentation for NyWater.info

This repository includes [git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) for the following repositories:

- [nyw_data](https://github.com/nywater/nyw_data) | [README]()

- [nyw_web_client](https://github.com/nywater/nyw_web_client) | [README]()

- [nyw_web_api](https://github.com/nywater/nyw_web_api) | [README]()

Each repository maintains its own README.md and deployment instructions - please consult each individual repository for development and deploy instructions.

### Updating submodules

1. Run `sh update.sh` - this will pull the latest changes for each repository. Commit and merge the changes to this repository ([nywater.info](https://github.com/nywater/nywater.info)).

### Deployment

These are the instructions to deploy the entire NyWater.info stack. We assume basic knowledge of server provisioning and dependency installation.

1. Provision a server (we use [DigitalOcean](https://www.digitalocean.com/)) running Ubuntu at version `16.04` with the following:
    - [Docker](https://www.docker.com/)
    - [Node.js](https://nodejs.org/)
    - [npm](https://www.npmjs.com/)
    - [nginx](https://www.nginx.com/)

2. Run the deploy instructions in the following submodules (order-specific)
    - `nyw_data`
    - `nyw_web_api`
    - `nyw_web_client`

3. Copy the client build to `/www` with the following commands:
    - `cp ~/nyw_deploy/nyw_web_client/dist/index.html /www/index.html`
    - `cp -R ~/nyw_deploy/nyw_web_client/dist/static /www/`

4. Copy `nywater.info.NGINX` to `/etc/nginx/sites-enabled/nywater.info`

5. Run `sudo service restart nginx`

### Documentation
- API documentation is available at [nywater.info/docs](http://nywater.info/docs)
