# Anotações do Laboratório AWS CloudFormation

## Descrição geral
Durante o laboratório, criei **stacks** no **AWS CloudFormation** por meio do upload de templates em formato **YAML**.  
O objetivo foi praticar a automação de infraestrutura (IaC) e entender o processo de criação de recursos como **instâncias EC2**, **servidores Apache**, **firewalls** e **buckets S3**.

---

## Processo de criação da Stack

### 1. Upload do Template
- O primeiro passo foi fazer o **upload de um template YAML** para o CloudFormation.  
- O templates descreviam a criação de **instância EC2 simples**, um **servidor Apache** e também a **configuração de regras de firewall**.

---

### 2. Definição do Nome da Stack
- Após o upload, escolhi um **nome para a stack**, no exemplo, o nome definido foi `laboratorio-ec2`.  
- Também é possível incluir **parâmetros personalizados**, mas neste caso o exemplo era opcional.

---

### 3. Configuração de Etiquetas (Tags)
- Na etapa seguinte, podemos adicionar **etiquetas (tags)** para facilitar a organização dos recursos.  
- As opções adicionais de configuração foram deixadas como **opcionais**.

---

### 4. Revisão da Stack
- Antes de criar a stack, o CloudFormation exibe uma página de **revisão** com o resumo de todos os recursos que serão criados.  
- Nessa etapa, também é possível visualizar a **URL do arquivo YAML** que foi enviado.

---

## Templates utilizados

### Template da EC2
- Definia a **zona de disponibilidade**, a **imagem (AMI)** e o **tipo de instância** (`t2.micro`).

### Template do Apache
- Seguia o mesmo padrão da EC2, mas incluía também uma **URL** para a instalação do servidor web Apache.

### Template do Firewall
- Criava uma **pilha (stack)** para definir regras de segurança, controlando o tráfego de entrada e saída.

---

## Erros encontrados
- **Nenhuma das três stacks (EC2, Apache, Firewall)** foi criada com sucesso.  
- A análise inicial indicou que o erro estava **relacionado a configurações da conta AWS**.  
- Mesmo alterando a **máquina e a região**, o erro persistiu.

---

## Teste com Bucket S3
- Em seguida, criei uma nova stack simples utilizando um **template YAML para criação de um bucket S3**.  
- Fiz o upload do arquivo diretamente no painel do CloudFormation e **a criação foi bem-sucedida**.  
- Após confirmar a criação do bucket, excluí todos os recursos ao finalizar o teste.

---

## Conclusão
- O laboratório demonstrou na prática o uso de **Infraestrutura como Código (IaC)** com CloudFormation.  
- Mesmo com falhas nas stacks iniciais, foi possível compreender o fluxo completo: **criação, verificação e exclusão** de recursos.  
- A criação bem-sucedida do **bucket S3** confirmou a configuração correta do serviço e consolidou o aprendizado sobre templates YAML.

---
## Template YAML – Criação de um bucket S3

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: "Laboratório mínimo - Criação de um bucket S3 via CloudFormation"

Resources:
  MeuBucketSimples:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: meu-bucket-simples-123456  # escolha um nome único

Outputs:
  NomeDoBucket:
    Description: "Nome do bucket criado"
    Value: !Ref MeuBucketSimples




