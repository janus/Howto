# How to run gitcoin web locally on your computer

*Check that you have Docker and Docker-compose properly installed*
```shell
docker --version
Docker version 18.09.7, build 2d0083d

docker-compose --version
docker-compose version 1.24.1, build 4667896b
```
The above worked for me.

### Installation of Docker and Docker-compose
1. Install [Docker](https://docs.docker.com/)
1. Install [Docker-compose](https://docs.docker.com/compose/install/)


#### Clone Gitcoin web repo and rename environment file
```shell
git clone https://github.com/gitcoinco/web.git && cd web
cp app/app/local.env app/app/.env
```

## Starting Gitcoin server and user app

```shell
docker-compose up -d --build
```

The above would create a background daemon when it finished installation. It takes pretty long time, mine was about an hour plus. The good news is that it runs on its own. If you have error while running this it is likely to come from docker and docker-compose.

![alt text](images/screenshot1.png "Installation screenshot")

![alt text](images/screenshot2.png "Installation screenshot")

When installation is completed, just point your browser to  `http://localhost:8000/`.
Note that with the above installation Gitcoin server runs as a service and its always there. You can stop it using `kill process`, docker-compose to stop it  or other means.

![alt text](images/Screenshoot_server1.png "Running screenshot")

![alt text](images/Screenshoot_server2.png "Running screenshot")

![alt text](images/Screenshoot_server4.png "Running screenshot")

![alt text](images/Screenshoot_server5.png "Running screenshot")


## Want to continue having fun?
Run:
```shell
make

autotranslate                  Automatically translate all untranslated entries for all LOCALES in settings.py.
build                          Build the Gitcoin Web image.
collect-static                 Collect newly added static resources from the assets directory.
compilemessages                Execute compilemessages for translations on the web container.
compress-images                Compress and optimize images throughout the repository. Requires optipng, svgo, and jpeg-recompress.
cypress                        Open cypress testing UI
eslint                         Run eslint against the project directory. Requires node, npm, and project dependencies.
fix-eslint                     Run eslint --fix against the project directory. Requires node, npm, and project dependencies.
fix                            Attempt to run all fixes against the project directory.
fix-isort                      Run isort against python files in the project directory.
fix-stylelint                  Run stylelint --fix against the project directory. Requires node, npm, and project dependencies.
fix-yapf                       Run yapf against any included or newly introduced Python code.
fresh                          Completely destroy all compose assets and start compose with a fresh build.
get_django_shell               Open a standard Django shell.
get_ipdb_shell                 Drop into the active Django shell for inspection via ipdb.
get_shell_plus                 Open a standard Django shell.
load_initial_data              Load initial development fixtures.
login                          Login to Docker Hub.
logs                           Print and actively tail the docker compose logs.
makemessages                   Execute makemessages for translations on the web container.
migrate                        Migrate the database schema with the latest unapplied migrations.
migrations                     Generate migration files for schema changes.
pgactivity                     Run pg_activivty against the local postgresql instance.
pgtop                          Run pg_top against the local postgresql instance.
push                           Push the Docker image to the Docker Hub repository.
pytest-pdb                     Run pytest with pdb support (Backend)
pytest                         Run pytest (Backend)
stylelint                      Run stylelint against the project directory. Requires node, npm, and project dependencies.
tests                          Run the full test suite.
update_fork                    Update the current fork master branch with upstream master.
update_stable                  Update the stable branch with master.

```

These are commands that you can use to play with Gitcoin web. However, they are for developer. If you want to play around some may need some special docker setup. `make build` uses  docker experimental functions.
```shell
sudo nano /etc/docker/daemon.json
```
Copy and paste
```
{ 
    "experimental": true 
} 
```