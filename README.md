## Tecnologias

O Objetivo desse projeto é colocar em prática as seguintes tecnologias:

- Docker
- Kubernetes
- Pipelines com Github Actions
- Monitoramento com Prometheus e Grafana

## Depois que seu ambiente docker e kubernetes estiver configurado

você precisa ter o <a href="https://community.chocolatey.org/packages/k3d" target="_blank">k3d</a> instalado na sua máquina

Execute esse Comando de criação do cluster Kubernetes com o K3D

```
k3d cluster create meucluster --servers 3 --agents 3 -p "30000:30000@loadbalancer"
```

 Deploy da Aplicação aplique os manifests criados no cluster Kubernetes local
```
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/prometheus.yaml
```

Verifique se a aplicação está em execução
```
kubectl get pods
```

Você vai colar essa url no seu navegador
```
http://localhost:30000/
```

Execute esse comando para acessar prometheus
```
kubectl --namespace default port-forward service/prometheus-server 9090:80
```

Você vai colar essa url no seu navegador
```
http://localhost:9090/
```

Execute esse comando para acessar grafana
```
kubectl --namespace default port-forward svc/grafana 3000:80
```

Você vai colar essa url no seu navegador
```
http://localhost:3000/
```

Para pegar a senha do usuário admin grafana
```
kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```

Se você estiver com dificuldade para pegar a senha do usuário admin grafana em um ambiente windows execute esse comando
```
$base64password = kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}"
[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($base64password))
```
