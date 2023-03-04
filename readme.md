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
