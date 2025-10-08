# Estudo de AWS CloudFormation

Este repositório é um material de estudo sobre **AWS CloudFormation**, focado em criar infraestrutura de forma automática e organizada usando templates YAML.

## O que é CloudFormation

O **CloudFormation** é um serviço da AWS que permite criar e gerenciar recursos da nuvem usando **infraestrutura como código (IaC)**.  
Ou seja, em vez de criar recursos manualmente pelo console da AWS, você escreve **templates** e a AWS cria **stacks** automaticamente com todos os recursos definidos.

### Conceitos importantes
- **Template**: arquivo YAML ou JSON que define os recursos que você quer criar.
- **Stack**: o conjunto de recursos criados a partir de um template.
- **Outputs**: informações que o template retorna depois que a stack é criada (ex: IP da EC2, nome do bucket S3).
- **Parâmetros (Parameters)**: permitem passar valores para o template na hora da criação da stack, como nome do KeyPair ou tipo de instância.
- **Recursos (Resources)**: tudo que será criado na AWS, como EC2, S3, IAM User, Security Group ou VPC.
- **Propriedades (Properties)**: configurações específicas de cada recurso, como porta aberta no Security Group ou nome do bucket S3.
- **Dependências (DependsOn)**: indica que um recurso deve ser criado após outro.
- **Funções intrínsecas (Intrinsic Functions)**: funções especiais usadas dentro do template:
    - `!Ref` → retorna o ID ou valor de um recurso ou parâmetro.  
    - `!GetAtt` → retorna atributos de um recurso, como IP da EC2.  
    - `!ImportValue` → importa valores exportados por outra stack. 

## Templates criados neste repositório

1. **EC2 para estudo**
   - Cria uma instância **t2.micro** na AWS.
   - Pode ver o IP público da EC2 nos Outputs.

2. **Firewall simples**
   - Cria um **firewall** conectado à VPC da EC2.
   - Serve para estudo de como os firewalls funcionam na AWS.

3. **EC2 com Apache**
   - Cria uma EC2 e instala automaticamente o **Apache (HTTPD)**.
   - Permite acessar a página padrão via navegador, só para estudo.

4. **EC2 + IAM + S3**
   - Cria uma EC2, um **usuário e grupo IAM**, e um **bucket S3**.
   - Ideal para estudar como diferentes recursos da AWS podem ser criados juntos.

## Como usar
1. Abra o **AWS CloudFormation** no console.
2. Clique em **Create Stack**.
3. Faça upload do template YAML que você quer usar.
4. Aguarde até a stack ser criada e confira os **Outputs** para ver informações como IP da EC2 ou nome do bucket S3.

## Observações
- Todos os templates aqui são **para estudo**.  
- Alguns templates não usam KeyPair, então não é possível acessar a EC2 via SSH.  
- O objetivo é aprender **infraestrutura como código** e como a AWS cria recursos automaticamente.

### Modelos prontos e diferença entre CloudFormation e Terraform

Aqui no repositório você encontra **templates prontos do CloudFormation** para estudo, tipo:  
- EC2 simples  
- EC2 com Apache  
- Firewall  
- S3  
- IAM User e Group  

Esses modelos são pra você **subir a infraestrutura automaticamente** sem precisar criar tudo na mão no console da AWS.  

#### Diferença entre CloudFormation e Terraform

- **CloudFormation** é da AWS, feito só pra criar recursos na AWS. Você escreve **templates YAML ou JSON**, sobe a stack, e a AWS cria tudo pra você.  
- **Terraform** é da HashiCorp, funciona com várias nuvens (AWS, Azure, GCP…) e também com serviços fora da nuvem. Você escreve **arquivos HCL**, e ele gerencia a infraestrutura, incluindo alterações e atualizações.  


