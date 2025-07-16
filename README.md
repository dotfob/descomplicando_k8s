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
  
## Configurações básicas para melhor usabilidade:

```
kind completion zsh > ~/.kube/completion.zsh.inc
echo "alias k='kubectl'" >> ~/.zshrc
echo "source ~/.kube/completion.zsh.inc" >> ~/.zshrc
source ~/.zshrc
```


