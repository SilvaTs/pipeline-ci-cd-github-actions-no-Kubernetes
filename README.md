## Tecnologias

O Objetivo desse projeto é colocar em prática as seguintes tecnologias:

- Docker
- Kubernetes
- Pipelines inteligentes com Github Actions
- Monitoramento com Prometheus e Grafana

## Depois que seu ambiente docker e kubernetes estiver configurado

você precisa ter o <a href="https://community.chocolatey.org/packages/k3d" target="_blank">k3d</a> instalado na sua máquina

Execute esse Comando de criação do cluster Kubernetes com o K3D

```
k3d cluster create meucluster --servers 3 --agents 3 -p "30000:30000@loadbalancer"
```

Você vai colar essa url no seu navegador
```
http://localhost:30000/
```


