# Taski

Приложение для планирования своих задач.

1. Cобрать образы: docker-compose build
2. Как запустить локально: docker-compose up
3. развернуть в Kubernetes: kubectl apply -f k8s/
4. Добавить секреты и configmap для подключения к БД и Docker в k8s:

```
kubectl create secret generic db-credentials \
 --from-literal=DB_USER=myuser \
 --from-literal=DB_PASSWORD=mypassword \
 --from-literal=DB_NAME=mydatabase
```

```
kubectl create configmap db-config \
 --from-literal=DB_HOST=db \
 --from-literal=DB_PORT=PORT
```

```
kubectl create secret docker-registry my-dockerhub-secret \
 --docker-username=mydockerhubusername \
 --docker-password=mydockerpassword \
 --docker-email=myemail@example.com
```

5.  В корне проекта создать .env файл, пример - .env.example
6.  Для корректной работы workflows добавить секреты DOCKER_USERNAME, DOCKER_PASSWORD, DB_USERNAME, DB_PASSWORD, DB_NAME в настройках репозитория на github.
