## TestLab Quick Start

### Clone the TestLab GitHub repo
```
git clone https://github.com/TestL-ab/testlab-docker.git
cd testlab-docker
```

### Launch the TestLab service on the localhost or server of your choice

run `docker-compose up -d` to launch TestLab in detached mode

run `docker-compose down` to spin down and remove the stopped container


### Launch the TestLab service on the AWS Elastic Container Service

To deploy to ECS using docker compose, you need to have set up a user with admin persmissions on an AWS account.

If you have not already done so, run the `docker context create ecs myecscontext` command to create an Amazon ECS Docker context named `myecscontext`. If you have already installed and configured the AWS CLI, the setup command lets you select an existing AWS profile to connect to Amazon.

Make sure you are in the ecs context by using `docker context use myecscontext`.

Run `docker compose up` to start the application on the ECS, and `docker compose down` to stop the application.

`docker compose ps` shows the status of the containers and the address where they can be reached.

### View the TestLab Application

The TestLab Application can be viewed at `http://localhost:3000` or at the 3000 port of the public IP address of your server.
