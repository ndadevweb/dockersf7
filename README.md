Create a folder app/

launch the command below

docker-compose build --build-arg HOST_UID=$(id -u) --build-arg HOST_GID=$(id -g)

docker-compose up -d

To install symfony 7

docker exec php_service composer create-project symfony/skeleton:"7.0.*" .

docker exec php_service composer require webapp

To create a new controller, entity, etc

docker exec -it php_service symfony consoke make:controller
docker exec -it php_service symfony consoke make:entity