# MICROSSERVIÇO PRODUTOS EKS

Este repositório contém a configuração para o microserviço de produtos, utilizando Kubernetes em um ambiente AWS EKS. O projeto inclui arquivos YAML para deploy e gerenciamento dos recursos relacionados ao microserviço.

## Estrutura do Projeto

### `kubernetes/Products/`

Contém os arquivos YAML necessários para configurar o microserviço de produtos no Kubernetes:

- **ClusterRole.yaml**: Define permissões de acesso para o microserviço no cluster.
- **ClusterRoleBinding.yaml**: Liga as permissões definidas no ClusterRole ao microserviço.
- **products-configmap.yaml**: Configurações de ambiente do microserviço.
- **products-deployment.yaml**: Define o deployment do microserviço no cluster.
- **products-hpa.yaml**: Configura o Horizontal Pod Autoscaler (HPA) para ajustar automaticamente a quantidade de réplicas.
- **products-service.yaml**: Serviço Kubernetes para expor o microserviço.

## Requisitos

- **Docker Desktop** com Kubernetes habilitado.
- **Kubectl** instalado. [Instruções](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- **AWS CLI** configurado com credenciais válidas. [Instruções](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)

## Como Executar

### Passo 1: Configurar o Cluster Kubernetes

1. Certifique-se de que o cluster EKS já foi provisionado e está funcional. Você pode utilizar Terraform ou outra ferramenta para configurar o EKS.

### Passo 2: Aplicar os Recursos do Microserviço

Execute o comandos abaixo para aplicar os arquivos YAML e configurar o microserviço no cluster:

```bash
kubectl apply -f kubernetes/Products
```

### Passo 3: Acessar o Microserviço

1. Após o deployment, verifique os serviços rodando no cluster:

```bash
kubectl get services
```

2. Utilize o endereço de IP do serviço para acessar o microserviço de produtos.

## Observações
- **Configuração de HPA:** O arquivo products-hpa.yaml ajusta automaticamente o número de réplicas com base na carga do microserviço. Certifique-se de que os recursos de CPU e memória estejam configurados corretamente.

- **ConfigMap:** O arquivo products-configmap.yaml contém as variáveis de ambiente necessárias para a execução do microserviço. Ajuste conforme necessário para o seu ambiente.

## Licença
Este projeto está sob a licença MIT. Consulte o arquivo LICENSE para mais informações.