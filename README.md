## This repo has been built base on the laradock
### Consist of:
+ php-fpm (port 9000)
+ nginx (port 80, 443)
+ mysql (port 3306)
+ phpmyadmin (http://localhost:5050)
+ redis (port 6379)
+ redis-webui (http://localhost:9987)
+ ngrok (http://localhost:4040)

## Precondition
+ Installed docker && docker-compose (latest version)
+ And your hands (just kidding :D)

## How to use
+ Go to docker repo
```
cd path/to/s5y-docker
```
+ Copy env-example && change the configs
```
cp env-example .env (Check and change the ports configs if already use it)
```
+ Create and start containers
```
docker-compose up -d
```
+ Go to workspace
```
docker exec -it -u laradock s5y_workspace_1 bash
// docker-compose exec -u laradock workspace bash
```
+ Finally, using composer to install laravel project
+ Config .env like below:
```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=s5y
DB_USERNAME=s5y
DB_PASSWORD=none
```
## Notes
+ phpmyadmin
```
http://localhost:5050
user: s5y
password: none
```
+ redis web ui
```
localhost:9987
user: s5y
password: none
```
+ ngrok
```
http://localhost:4040
```
+ Show link ngrok
```
curl -s $(docker port s5y_ngrok_1 4040)/api/tunnels/command_line | python -c "import sys, json; print json.load(sys.stdin)['public_url']"
```
+ Stop and remove containers, networks, images, and volumes
```
docker-compose down
```
## Short command
+ Go to workspace and move to project (s5y-project)
```
./bin/s5y ga
```
+ Show ngrok link
```
./bin/s5y ngrok
```

