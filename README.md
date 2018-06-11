BerryTube
=========

Before running for the first time
---------------------------------

Run `git submodule update --init --remote` to pull in berrymotes.

Download [the emote data](https://cdn.berrytube.tv/berrymotes/data/berrymotes_json_data.json) and place it in `berrymotes/data/`. Avoid running the scraper, so that Reddit doesn't get mad at us.

Copy `.env.sample` to `.env` and tweak the values. All the domains themselves and the main domain prefixed with www. must point to the server.

Run `docker volume create caddy` to create a shared volume for storing certificates. This can be shared across multiple instances to prevent hitting Let's Encrypt rate limits.


Running
-------

To run (or apply changes): `docker-compose up -d --build`

To stop and remove containers (keeps data): `docker-compose down`

Note that the `web` directory is mounted directly into the containers (as read-only), so any changes there will get applied immediately.


Database
--------

The database is placed in a docker volume. To get an SQL prompt, run `docker exec -it berrytube_mysql_1 mysql -uberrytube -pberrytube berrytube`.
