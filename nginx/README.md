```
docker build -t luckyjing/nginx .
docker run -p 8080:80 --rm [--volumes-from CONTAINER_NAME] luckyjing/nginx
```
