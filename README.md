# Installation

- Copy the `docker-reverse-proxy` folder to the root of your project folders.
- Go in that folder and run `docker-compose up -d`.
- Copy the `docker` folder and the docker-compose.yml file to your project folder.
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
- Run `docker-compose up -d` in the project folder.

---

You can access the app container by running `docker exec -it myproject_app bash` when the `DOCKER_PREFIX` is `myproject`.