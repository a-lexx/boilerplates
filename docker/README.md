### setup (script)
curl -fsSL https://get.docker.com -o get-docker.sh

## check (script)
sudo sh ./get-docker.sh --dry-run

### container run
docker run -d -p 80:80 --restart=always --name nginx-proxy nginx

### containers started list
docker ps
### containers list all
docker ps -a

### images list
docker images
docker image ls

### images deletion
docker rmi grafana/grafana 
docker rmi $(docker images -a -q)

### Вход в консоль контейнера:
docker exec -it nginx-proxy bash

### Просмотр логов контейнера:
docker logs nginx-proxy
docker logs --tail 100 nginx-proxy

### Статистика потребляемых ресурсов контейнера или группы контейнеров:
docker stats grafana7
docker stats container1 container2
docker stats grafana7 --format "table {{.Name}}\t{{.CPUPerc}}\t{{.MemUsage}}"

### Просмотр запущенных процессов в контейнере:
docker top grafana7

### Информация о контейнере:
docker inspect nginx-proxy

### Выполнить команду в контейнере:
docker exec -it nginx-proxy /usr/sbin/nginx -s reload
docker exec -i docker-mariadb-1 mysql -uDB_USER -pDB_PASSWD MyDBdev < /tmp/MyDBdev.sql

### Очистить неиспользуемые данные:
docker system prune

### Очистить неиспользуемые данные (containers, volumes, networks и images):
docker system prune -a -f --volumes

### Проверить занимаемое докером место:
docker system df

### logs
grep -C1 -e ipwhois -e forward `docker inspect --format='{{.LogPath}}' web-platform.web.1` | jq

### Docker linter
docker run --rm -i hadolint/hadolint < Dockerfile

### Docker heredocs
https://www.docker.com/blog/introduction-to-heredocs-in-dockerfiles/
