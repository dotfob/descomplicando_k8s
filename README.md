# descomplicando_k8s

## Day-1
Dia de instalar cluster k8s usando o kind. O Kind faz uso do Docker para criar um cluster local, criando containers para fazer o papel de ControlPlanes e Workers.
Exemplo de config file:
```
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
- role: worker
```
Comando para aplicar:
```
  kind create cluster --config config.yaml --name foblab
```
## Instalação do kubectl para linux 
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
mv kubectl /usr/local/bin/
```

## Configurações básicas para melhor usabilidade:

```
kind completion zsh > ~/.kube/completion.zsh.inc
echo "alias k='kubectl'" >> ~/.zshrc
echo "source ~/.kube/completion.zsh.inc" >> ~/.zshrc
source ~/.zshrc
```
## Exemplos de Comandos básicos
get:
```
k get ...
  clusters
  nodes
  pods
  services
  deployments
  ...
```

run:
```
kubectl run --image nginx --port 80 --name webserver
```
delete:
```
kubetl delete ...
  pods
  services
  deployments
  ....
```

expose:
```
kubectl expose pods webserver --type NodePort
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
```

exec: 
```
 kubectl exec -ti webserver -- bash
 kubectl exec -ti webserver -- curl http://localhost:8080 
```

dry-run: (gerar arquivo yalm)
```
kubectl run --image nginx --port 80 webserver --dry-run=client -o yaml > nginx.yaml
kubectl apply -f nginx.yaml
```
## Fontes
https://kind.sigs.k8s.io/docs/user/quick-start/
https://kubernetes.io/pt-br/docs/tasks/tools/install-kubectl-linux/
