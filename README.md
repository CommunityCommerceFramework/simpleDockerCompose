
## Purpose of this project

simplified docker-compose setup to create a magento supporting environment suited for Development, Testing and Benchmark usecases


## How to use it

start up an environment
`docker-compose up -d`

open the phpinfo via http://172.17.0.1:8081/info.php (local IP may or may not differ, but thats mine)


## ToDo

the /data/ directory should maybe get added to .gitignore  
Or we add another directory/port mapping to the config for custom applications.

Adding informations about the configured domains in nginx

add informations about the custom php.ini config
