
# Running Verdaccio a Self Hosted Private NPM with Docker
Verdaccio is a lightweight private npm registry that can be run locally. 

### Clone the repo
I created a repo with the docker-compose file for running the application in the docker container. 

**Repo:** [https://github.com/Docker-X/verdaccio-docker-compose](https://github.com/Docker-X/verdaccio-docker-compose)

### Run the application:
Open a terminal, navigate to the directory containing the docker-compose.yml file, and run the following command:
```bash
cd verdaccio-docker-compose/
docker-compose up  -d
```
Verdaccio will be accessible at [http://localhost:4873](http://localhost:4873)

### How to use the npm package manager
Get into the container
```bash
docker exec  -it  verdaccio  sh
```
To publish your first package just:
1. Create user
```bash
$ docker exec  -it  verdaccio  sh # This command will take you into the container
~ $ npm adduser  --registry  http://localhost:4873/
npm notice Log in on http://localhost:4873/
Username: balu
Email: (this IS public) jinna.baalu@gmail.com

Logged in on http://localhost:4873/.
```

2. Go to the project to publish

```bash
mkdir nodejs-app
cd my-nodejs-app
echo "console.log('Hello, World!');" > app.js
npm init -y
node app.js

npm login  --registry  http://localhost:4873/
npm publish  --registry  http://localhost:4873/
```

Go To  [http://localhost:4873](http://localhost:4873) and refresh you will see your package available

### Stop the application:
To stop the running containers, use the following command:
```bash
docker-compose down
```
