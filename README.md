# Taski

Приложение для планирования своих задач.

1. **Собрать образы**:
    ```bash
    docker-compose build
    ```
2. **Запустить локально**:

    ```bash
    docker-compose up
    ```

3. **Развернуть в Kubernetes**:

    ```bash
    kubectl apply -f k8s/
    ```

4. **Добавить секреты и configmap для подключения к БД и Docker в k8s**:

    - Создание секрета для базы данных:

    ```bash
    kubectl create secret generic db-credentials \
     --from-literal=DB_USER=myuser \
     --from-literal=DB_PASSWORD=mypassword \
     --from-literal=DB_NAME=mydatabase
    ```

    - Создание configmap для параметров базы данных:

    ```bash
    kubectl create configmap db-config \
     --from-literal=DB_HOST=db \
     --from-literal=DB_PORT=5432
    ```

    - Создание секрета для Docker:

    ```bash
    kubectl create secret docker-registry my-dockerhub-secret \
     --docker-username=mydockerhubusername \
     --docker-password=mydockerpassword \
     --docker-email=myemail@example.com
    ```

5. В корне проекта создать .env файл, пример - .env.example
6. Для корректной работы workflows добавить секреты DOCKER_USERNAME, DOCKER_PASSWORD, DB_USERNAME, DB_PASSWORD, DB_NAME в настройках репозитория на github. (Settings > Secrets and variables > Actions)
