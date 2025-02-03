

### 1. Примените измененный манифест:

Теперь примените этот измененный манифест для развертывания Tarantool в Minikube.

```bash
kubectl apply -f tarantool-deployment.yaml
```

### 2. Подключение к Tarantool

Для подключения к Tarantool, если вы хотите работать непосредственно с базой данных через консоль Tarantool, используйте команду:

```bash
tarantoolctl connect 192.168.49.2:30312
```


### 3. Подключение извне через Minikube

Если вы подключаетесь к Minikube извне, используйте IP-адрес Minikube и порт, который был выделен для вашего сервиса в Kubernetes (NodePort). Для этого выполните команду:

```bash
minikube service tarantool-service --url
```

После этого вы получите URL, например, `http://192.168.49.2:30312`. Вы можете использовать его для подключения к вашему сервису Tarantool извне.


### 4. Установка Helm-чарта

После того как вы создали структуру и все файлы, вы можете установить чарт с помощью команды:

```bash
helm install my-tarantool-release ./my-tarantool-chart
```

Где `my-tarantool-release` — это имя вашего релиза, а `./my-tarantool-chart` — путь к директории, содержащей ваш чарт.

### 5. Обновление значений

Если вам нужно изменить параметры, такие как количество реплик или порт, вы можете изменить их в файле `values.yaml` и обновить релиз:

```bash
helm upgrade my-tarantool-release ./my-tarantool-chart
```
