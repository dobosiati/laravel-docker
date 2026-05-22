# Installation

- Copy the `docker-reverse-proxy` folder to the root of your project folders.
- Go in that folder and run `docker network create web` and `docker-compose up -d`.
- Copy the `docker` folder and the `docker-compose.yml` file to your project folder.
- Make sure that the `.env` file has these variables:
  - `DOCKER_PREFIX`
  - `APP_URL` and `MAIL_URL`
    - Remember to add them to your `hosts` file.
  - `DB_HOST` has to be `mysql`
  - `DB_DATABASE`
  - `DB_ROOT_PASSWORD` (optional)
    - Default: `root`
  - `DB_USERNAME`
  - `DB_PASSWORD`
  - `DB_PORT` (optional)
    - Default: `3306`
  - `REDIS_HOST` has to be `redis`
  - `REDIS_PORT` has to be `6379`
- Run `docker-compose up -d` in the project folder.
- You will have to add www-data ownership to the project folder inside the container: `chown -R www-data:www-data /var/www`.

---

You can access the app container by running `docker compose exec app sh` in the project folder.