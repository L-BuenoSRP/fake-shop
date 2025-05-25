# Comandos executados para construção dos clusters e deploys com kubernetes

## Instalações necessarias

#### WSL 

[Instalação WS - Medium](https://medium.com/@liu-qilong/a-complete-guide-to-setup-wsl-windows-subsystem-for-linux-4547e88b6cdb)

[Instalação WS - Franciscojsc github](https://gist.github.com/franciscojsc/127da118d12a0b83c064407c5e860d71)

[Instalação WS - Microsoft](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#configure-global-options-with-wslconfig)

[Instalar Docker Desktop](https://docs.docker.com/desktop/setup/install/windows-install/)

[Docker com WSL](https://learn.microsoft.com/pt-br/windows/wsl/tutorials/wsl-containers)

[Instalar kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

[k3d](https://k3d.io/)

## Comandos

#### Cria containers
`k3d cluster create`

#### Cria um cluster com nome definido
`k3d cluster create my-cluster`

#### Cria um cluster com a quantidade de servers(control-panes) e agends(worker-nodes)
`k3d cluster create my-cluster --servers 3 --agents 3`

#### Cria o cluster com o mapeamento de porta com loadbalancer
`k3d cluster create my-cluster --servers 3 --agents 3 -p "5000:30000@loadbalancer"`

#### Pega os nos rodando nos clusters
`kubectl get nodes`

#### Mostra quantos clusters tem
`k3d cluster list`

#### Deleta o cluster
`k3d cluster delete`

#### Deleta o cluster especifico
`k3d cluster delete my-cluster`

#### lista os recursos que pode criar no kubernets
kubectl api-resources

#### Para criar um objeto declarado no manifesto - Sobe o deployment no cluster
`kubectl apply -f k8s/deployment.yaml`

#### Remove o objeto declarado - remove o depoloyment e container
`kubectl delete -f k8s/deployment.yaml`


kubectl rollout undo deployment fakeshop

#### Consulta os pods
`kubectl get pod`

#### Consulta no comando do pod qual worker node esta com cada pod
`kubectl get pod -o wide`

#### Faz o mapeamento de portas entre o container de um pod e a maquina host(meu pc)
`kubectl port-forward pod/postgre-8598b6b9f9-thkgd 5432:5432`

#### Executa um comando de tempos em tempos(comando linux)
`watch 'kubectl get pod'`

#### Comando equivalente no windows
`while ($true) { kubectl get pod; Start-Sleep -Seconds 1 }`

#### Consulta os logs do pod usando o nome que esta registrado vindo do comando `kubectl get pod`
`kubectl logs pod-nome`

#### Visualiza detalhes do pod, como eventos, imagem usada, node, portas, etc
`kubectl describe pod fakeshop-784fbc4fb4-9v8hk`

#### Visualiza detalhes do node, como eventos,memoria, arquitetura, ips, etc
`kubectl describe node k3d-my-cluster-server-1`

#### Deleta o deployment
`kubectl delete deployment fakeshop`

#### Deleta o pod pelo nome(buscar com kubectl get pod)
`kubectl delete pod fakeshop-784fbc4fb4-9v8hk`

#### Busca os services
`kubectl get service`

#### Busca os deployments
`kubectl get deployment`

#### Busca os replicaset
`kubectl get replicaset`

#### Busca todos os objetos existentes
`kubectl get all`

#### Mapeia a porta para acesso externo na maquina hospedeira(funciona apenas em k3d / não funciona em ambiente cloud, nestes é necessario definir o service com mapeamento de loadbalancer na declaração do arquivo deployment)
`kubectl port-forward service/fakeshop 5000:5000`



#### Verifica o Status do Deployment: Após aplicar as mudanças, verifique o status do deployment para garantir que ele está usando a nova imagem.
`kubectl rollout status deployment/fakeshop`

#### Configure Git to Use LF Line Endings: You can configure Git to use LF line endings for all files in your repository. Create a .gitattributes file in the root of your repository with the following content:
>`# filepath: c:\Users\leand\Code\fake-shop\.gitattributes`
>
>`*.sh text eol=lf`

#### Dentro do WSL, baixa dependencias de uso do vscode pelo wsl e abre em um arquivo especifico no caminho /home/.kube/config
`code ~/.kube/config`
