This repo contains:

- Files to build the TestLab postgres container that includes the database and tables required for the TestLab Server
- `docker-compose.yml` that can be used to deploy the TestLab application to a user's localhost, virtual server, or AWS service (e.g., EC2 instance or ECS)

**To rebuild the postgres container**
`docker build .` from within the `pg` directory
If the schema is changed, the newly built container will need to be uploaded to AWS

**To launch the TestLab service on the server of your choice**
Include a `.env` file in the same directory as the `docker-compose.yml` that includes the following (include your own password for `PG_PASSWORD`):

```
PORT=3000
PG_DATABASE=TestLab
PG_PASSWORD=password
PG_USERNAME=postgres
```

run `docker-compose up -d` to launch TestLab in detached mode
run `docker-compose down` to spin down and remove the stopped container

**To launch the TestLab service on the AWS ECS**

Set up the `.env` file as described above, and store it in the same directory as the `docker-compose.yml` file.

To deploy to ECS using docker compose, you need to have set up a user on the AWS account that has admin permissions.

If you have not already done so, run the docker context create ecs myecscontext command to create an Amazon ECS Docker context named myecscontext. If you have already installed and configured the AWS CLI, the setup command lets you select an existing AWS profile to connect to Amazon.

Run `docker compose up` to start the application on the ECS, and `docker compose down` to stop the application.

`docker compose ps` shows the status of the containers and the address where they can be reached.
