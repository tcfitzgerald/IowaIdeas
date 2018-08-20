## About

IowaIdea petition application for the UI community. It has been forked from  https://github.com/ritstudentgovernment/PawPrints.git

## Installation
To get IowaIdea up and running, you must have Docker and Docker Compose installed on your machine.

### Building Containers
Once you have Docker installed, clone the repository.

``` git clone https://github.com/uiowa/IowaIdeas```

Next, copy the ```template.env``` file at the root of the project to ```.env``` and fill out the environment variables. When running the application locally, the ```SERVER_ENV``` variable should be set to ```local```. The defaults should be sufficient for running locally.

```cp template.env .env```

Once you have the env file, simply run
```docker-compose up``` from the root project directory. This will take a few minutes as it builds the containers.

To ensure that all the containers are running, simply run ```docker ps``` you should have an output similar to the following
```
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
beaf1081ae86        IowaIdea_worker    "python manage.py ru…"   20 minutes ago      Up 20 minutes                                IowaIdea_worker_1
71a8edb3235c        IowaIdea_web       "sh -c 'python manag…"   20 minutes ago      Up 20 minutes       0.0.0.0:8000->8000/tcp   IowaIdea_web_1
4170e6d57385        postgres:alpine     "docker-entrypoint.s…"   21 minutes ago      Up 20 minutes       5432/tcp                 postgres
508ad9ed3e43        redis:alpine        "docker-entrypoint.s…"   21 minutes ago      Up 20 minutes       6379/tcp                 IowaIdea_redis_1
```
### Generate mock data
If running the application for the first time, there will be no data in the database. To generate mock data, you must run the mockdata script.

Before running the script, ensure that the containers are up and grab the name of the web container. Refering to the output of ```docker ps``` above, the web container is named ```IowaIdea_web_1```.

Then to run the script, ```docker exec -it IowaIdea_web_1 python manage.py mockdata```. The script will take a while to run as it generates the mock data.

Finally, to view the app, simply navigate to http://localhost:8000
