# Fake Shop


## Instruções de execução

### CI/CD Pipeline - Fake Shop

Este repositório contém a configuração de uma pipeline CI/CD utilizando GitHub Actions para o projeto Fake Shop.

### Estrutura da Pipeline

A pipeline está definida no arquivo [`.github/workflows/main.yml`](.github/workflows/main.yml) e é composta por dois jobs principais: `CI` e `CD`.

#### CI (Continuous Integration)

Este job é responsável por:

1. Obter o código do repositório.
2. Fazer login no Docker Hub.
3. Construir e enviar a imagem Docker para o Docker Hub.

#### CD (Continuous Deployment)

Este job é responsável por:

1. Obter o código do repositório.
2. Configurar o contexto do Kubernetes utilizando o KubeConfig.
3. Aplicar as configurações do Kubernetes utilizando o manifesto `k8s/deployment.yaml`.

### Como Executar a Pipeline

A pipeline é executada automaticamente nos seguintes eventos:

- Push na branch `main`.
- Execução manual via `workflow_dispatch`.

#### Variáveis e Segredos Necessários

Certifique-se de configurar as seguintes variáveis e segredos no repositório:

- `DOCKERHUB_USERNAME`: Nome de usuário do Docker Hub.
- `DOCKERHUB_TOKEN`: Token de acesso do Docker Hub.
- `K8S_KUBECONFIG`: Configuração do KubeConfig para acesso ao cluster Kubernetes.

## Variável de Ambiente
DB_HOST	=> Host do banco de dados PostgreSQL.

DB_USER => Nome do usuário do banco de dados PostgreSQL.

DB_PASSWORD	=> Senha do usuário do banco de dados PostgreSQL.

DB_NAME	=>	Nome do banco de dados PostgreSQL.

DB_PORT	=>	Porta de conexão com o banco de dados PostgreSQL.
