### Run

```
# 启动minikube
minikube start

# 将当前shell的docker环境指向minikube内
eval $(minikube docker-env)

# 编译打包（docker镜像保存在minikube内）
mvn compile jib:dockerBuild

# 创建一个deployment
kubectl apply -f echo-deployment.yaml

# 创建一个service（暴露出deployment的端口）
kubectl expose deployment echo-boot --type=NodePort --port=8080

# 获得service的url
minikube service echo-boot --url

curl http://.....

# 横向扩展
kubectl scale deployment echo-boot --replicas=2

curl http://.....
```