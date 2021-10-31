# Задание 1: подключить для тестового конфига общую папку

Создадим конфиг пода с общей папкой:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: static-vol
spec:
  containers:
    - name: cont1
      image: nginx
      volumeMounts:
        - mountPath: "/static1"
          name: static
    - name: cont2
      image: praqma/network-multitool
      env:
          - name: HTTP_PORT
            value: "88"
      volumeMounts:
        - mountPath: "/static2"
          name: static
  volumes:
    - name: static
      emptyDir: {}

```
Попробуем создать файл через первый контейнер и прочитать его из второго:
![task](task1.png)

