# Installation

- Copy the `docker-reverse-proxy` folder to the root of your project folders.
- Go in that folder and run `docker-compose up -d`.
- Copy the `docker` folder and the docker-compose.yml file to your project folder.
- Make sure that the `.env` file has these variables:
  - `DOCKER_PREFIX`
  - `APP_URL`
    - With or without the `http://` or `https://`. Default is `https://`.
  - `MAIL_URL` (optional)
    - Default: `mail.${APP_URL}`.
    - Add this variable if you specify the `APP_URL` network protocol (etc.: `http://`).
  - `DB_DATABASE`
  - `DB_ROOT_PASSWORD` (optional)
    - Default: `root`
  - `DB_USERNAME`
  - `DB_PASSWORD`
