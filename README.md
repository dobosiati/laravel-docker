# Installation

- Copy the `docker-reverse-proxy` folder to the root of your project folders.
- Go in that folder and run `docker-compose up -d`.
- Copy the `docker` folder and the docker-compose.yml file to your project folder.
- Make sure that the `.env` file has these variables:
  - `DOCKER_PREFIX`
  - `APP_URL`
  - `MAIL_URL`
  - `DB_DATABASE`
  - `DB_ROOT_PASSWORD` (optional)
    - Default: `root`
  - `DB_USERNAME`
  - `DB_PASSWORD`
