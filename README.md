# Tutorial: Rodar R na Nuvem com AWS EC2 + Armazenar Arquivos no S3

Este guia destina-se a orientar iniciantes no uso de recursos da Amazon Web Services (AWS) para:

- Rodar scripts em R na nuvem (via EC2)
- Armazenar e acessar arquivos na nuvem (via S3)

---

## Etapa 1: Criar uma conta na AWS

- Acessar: https://aws.amazon.com/pt/
- Criar uma conta com e-mail e cartão de crédito internacional
- Acessar o console após a ativação: https://console.aws.amazon.com/

---

## Etapa 2: Configurar uma instância EC2

- Acessar: https://console.aws.amazon.com/ec2
- Selecionar “Executar instância”
- Escolher:
  - Imagem (AMI): Ubuntu Server 22.04 LTS
  - Tipo de instância: t2.micro (gratuita) ou t3.medium, m6i.large (pagas)
- Criar e baixar uma chave de acesso (.pem)
- Definir permissões de segurança:
  - Porta 22 (SSH)
  - Porta 8787 (RStudio Server, opcional)
- Iniciar a instância

---

## Etapa 3: Acessar a instância via terminal

```bash
ssh -i chave_do_aws.pem ubuntu@SEU-IP
```

---

## Etapa 4: Instalar o R e o RStudio Server

```bash
sudo apt update
sudo apt install r-base -y

wget https://download2.rstudio.org/server/jammy/amd64/rstudio-server-2023.06.2-561-amd64.deb
sudo apt install ./rstudio-server-2023.06.2-561-amd64.deb
```

- Acessar no navegador: http://SEU-IP:8787
- Utilizar o usuário padrão da instância ou criar um novo com `sudo adduser nome_usuario`

---

## Etapa 5: Armazenar arquivos no Amazon S3

- Acessar: https://s3.console.aws.amazon.com/s3/
- Selecionar “Criar bucket”
- Informar um nome único (ex: dados-r-projeto)
- Desativar o bloqueio de acesso público se necessário
- Confirmar a criação

Para subir arquivos:

```bash
aws s3 cp dados.csv s3://dados-r-projeto/
```

Para baixar:

```bash
aws s3 cp s3://dados-r-projeto/dados.csv .
```

---

## Etapa 6: Configurar o AWS CLI

```bash
sudo apt install awscli
aws configure
```

- Informar:
  - Access Key ID
  - Secret Access Key
  - Região (us-east-2 recomendado)
  - Formato padrão: json

---

## Etapa 7: Ler dados do S3 diretamente no R

```r
library(aws.s3)
obj <- get_object("dados.csv", bucket = "dados-r-projeto")
df <- read.csv(text = rawToChar(obj))
```

---

## Glossário de termos essenciais da AWS

| Termo       | Definição |
|-------------|-----------|
| **Instância (EC2)** | Máquina virtual criada na nuvem, como um servidor pessoal acessível remotamente. |
| **AMI (Amazon Machine Image)** | Imagem pré-configurada com sistema operacional e softwares para rodar na EC2. |
| **Chave (.pem)** | Arquivo de autenticação necessário para acessar a instância via terminal (SSH). |
| **S3 (Simple Storage Service)** | Serviço de armazenamento de arquivos na nuvem, tipo “HD virtual”. |
| **Bucket** | Pasta principal dentro do S3 onde os arquivos são organizados. |
| **CLI (Command Line Interface)** | Interface de linha de comando para interagir com os serviços da AWS. |
| **Role** | Conjunto de permissões atribuídas a serviços para acessar outros recursos da AWS. |
| **Região** | Local físico onde os servidores da AWS estão localizados (ex: us-east-1, sa-east-1). |
| **Latência** | Tempo de resposta entre o usuário e os servidores da AWS. Menor distância → menor latência. |
| **Tier Gratuito (Free Tier)** | Conjunto de serviços gratuitos da AWS por 12 meses, com limitações de uso. |

---

## Observações Finais

- Lembrar de parar a instância quando não estiver utilizando, para evitar cobranças:

```bash
aws ec2 stop-instances --instance-ids i-xxxxxxxxxxxx
```

- Recomendar criar scripts automatizados e configurar o agendamento de tarefas via `cron`.