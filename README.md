### https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-nested-stacks.html
# Nested Stacks AWS Cloudformation

### Nesse projeto foi desenvolvido Templates para a criação e atualização de instâncias EC2 Nested Stacks.

- ### The AWS :: CloudFormation :: Type Stack Nessa uma stack como um recurso em um modelo de nível superior.
 
- ### podemos adicionar valores de saída de uma pilha aninhada na stack raiz.
- ### Usamos a função fn :: getatt com o nome lógico das pilhas aninhadas e o nome do valor de saída na pilha aninhada.

## Step#0:

## S3 Bucket 

- ### Crie S3 Bucket
- ### Isso é necessário para fazer upload dos template da stack aninhados para S3.

## Step#1:



### VPC Nested Stack Template

- ### Create Parameters 
- ### Create Metadata 
- ### Create Resources 
  - ### Create VPC 
  - ### Create Subnets 
  - ### Create  Route Table 
  - ### Associate Subnet &  Route Table 
  - ### Create IGW 
  - ### Associate IGW to 
  - ### VPC
  - ### Create Route 
- ### Create Outputs 
- ### Test Template 
- ### Upload to S3

## Step#2:

### Root Stack Template

- ### Create Parameters 
- ### Create Resources 
  - ### Create VPC Stack 
  - ### Create EC2 Instance 
- ### Create Outputs

# Nested Stacks – Practice – Create Stack

## Step#3:  

## For VPC Nested Stack

- ### Create Root Stack 
- ### It automatically creates the vpc nested stack

### Root Stack ==============> VPC Nested Stack

# Nested Stacks – Practice – Create Stack


## Step#4:

### Security Group  Nested Stack Templat

- ### Create Parameters 
- ### Create Resources 
- ### Create Security Group 
- ### Criar Outputs

## Step#5:

### Root Stack Template

- ### Crie parâmetros
- ### Crie recursos
   - ### Criar VPC stack
   - ### Criar a instância do EC2
- ### Crie saídas
- ### Criar recurso
   - ### Crie segurança
   - ### grupo de stacks
   - ### Atualizar VM
   - ### Recurso da instância
   - ### Com grupo de segurança


## Step#6:

### Para Nested Stack de VPC

 ###  Crie Stack Root
- ### Criar automaticamente
- ### Criar a VPC da Nested Stack

## Para o grupo de segurança, Nested Stack Etapa 6:

- ### Atualize a stack root com novo template.

- #### Cria automaticamente o grupo de segurança nested stack 

## Vpc Nested Stack <========Root Stack========> Security Group Nested Stack

# Nested Stacks – Practice – Update Stack 2

## Step#7:

## Para a Nested Stack de VPC
  - ### Crie Stack Root
  - ### cria automaticamente o VPC nested stack

 ## Abordagem altamente recomendada
  - ### sempre execute atualizações da stack raiz
  - ### Nunca atualize as Nested Stack diretamente.

## Para o grupo de segurança, Nested Satack
- ### Atualize a stack root com novo modelo.
- ### Cria automaticamente o grupo de segurança nested stack

## For Nested Stack Updates

- ### Atualize a Nested Stack SG com nova regra de segurança.
- ### Faça o upload do novo template para S3
- ### Atualize a Stack root com o Template existente.

### VPC Nested Stack <=========Root Stack========> Security Group Nested Stack (Update Stack)

# Nested Stacks – Practice – Delete Stack

# Step#8:

- Recomendações
- Sempre exclua a stack raiz.
- Nunca exclua Nested Stack diretamente.
- Sempre que excluímos a stack raiz
nested stacks associadas terão sido
excluídas automaticamente.

## VPC Nested Stack <========Root Stack========> Security Group Nested Stack
##                           Root Stack <========Always Delete Root Stack

# Nested Stacks vs Outputs - Pending

- ### Uma Nested Stack é uma stack que você cria em outra stack usando o recurso AWS :: CloudFormation :: Stack (p. 954).Com nested stack, você implanta e gerencia todos os recursos de uma única stack.
- ### Você pode usar saídas de uma stack no grupo de nested stack como entrada para outra stack do grupo.Isso difere dos valores de exportação.
- ### Se você deseja isolar o compartilhamento de informações em um grupo de Nested Stack, sugerimos que você use Nestd stack.Para compartilhar informações com outras stacks (não apenas dentro do grupo de Nested Stacks), os valores de exportação.
- ### Por exemplo, você pode criar uma única stack com uma sub -rede e depois exportar seu ID.Outras stack podem usar essa sub -rede importando seu ID;Cada stack não precisa criar sua própria sub -rede.Observe que, desde que as stacks estejam importando o ID da sub -rede, você não poderá alterá -lo ou excluí -lo.