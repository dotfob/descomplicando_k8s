# descomplicando_k8s

## Day-1
Dia de instalar cluster k8s usando o kind. O Kind faz uso do Docker para criar um cluster local, criando containers para fazer o papel de ControlPlanes e Workers.
Exemplo de config file:
  `
  kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
- role: worker
  `

Comando para aplicar:
  kind create cluster --config config.yaml --name foblab

  
