Resumo Operacional: criar conta, configurar EC2 e operar com R

Para iniciar o uso da AWS com R de forma simples.

------------------------------

1. Criar conta na AWS

- Acessei: https://aws.amazon.com/pt/
- Quando tive dificuldade, acessei diretamente:
  https://us-east-2.signin.aws.amazon.com/oauth?... (atalho direto para login)
- Criei a conta com meu e-mail e um cartão de crédito internacional (usei o Nubank)
- Depois que minha conta foi ativada, entrei no console: https://console.aws.amazon.com/

Caminho: navegador > AWS > criar conta > console

------------------------------

2. Criar instância EC2

- Acessei: https://console.aws.amazon.com/ec2/
- Cliquei em “Executar instância”
- Escolhi a AMI: Ubuntu Server 22.04 (64-bit x86)
- Selecionei o tipo t2.micro (Free Tier), mas depois usei uma instância mais forte para rodar os dados
- Criei e baixei a chave `.pem`. Salvei num lugar seguro
- (Não fiz) liberação das portas 22 e 8787. Pulei essa etapa
- Iniciei a instância e copiei o IP público

Caminho: Console > EC2 > Instâncias > Executar instância

------------------------------

3. Acessar via terminal

Comando usado no PowerShell:

ssh -i minha_chave.pem ubuntu@MEU-IP

No Windows: pressionei Win + R, digitei "powershell", naveguei até a pasta da chave e executei o SSH

------------------------------

4. Instalar R na instância

Depois de logado via SSH na EC2, rodei:

sudo apt update
sudo apt install r-base -y

------------------------------

5. (Opcional) Instalar RStudio Server

Ainda dentro da instância, executei:

wget https://download2.rstudio.org/server/jammy/amd64/rstudio-server-2023.06.2-561-amd64.deb
sudo apt install ./rstudio-server-2023.06.2-561-amd64.deb

Depois, abri no navegador: http://MEU-IP:8787

------------------------------

6. Configurar AWS CLI

Instalei e configurei assim:

sudo apt install awscli
aws configure

Informei minha Access Key, Secret Key, região (usei us-east-2) e o formato como json

------------------------------

7. Criar bucket no S3

- Acessei: https://s3.console.aws.amazon.com/s3/
- Cliquei em “Criar bucket”
- Dei um nome único
- Quando precisei, alterei as permissões de acesso público

Caminho: Console > S3 > Criar bucket

------------------------------

8. Subir ou baixar arquivos

Com a AWS CLI já configurada, usei:

aws s3 cp arquivo.csv s3://nome-do-bucket/
aws s3 cp s3://nome-do-bucket/arquivo.csv .

------------------------------

Esse foi o caminho que segui para começar a trabalhar com Py / R usando a AWS. Vou detalhar nos próximos tópicos.. Acrescentei uma lista de comandos uteis na seção abaixo (9).

------------------------------

9. Comandos úteis em PowerShell

Para consultar os principais comandos que usei no terminal para operar EC2 e S3 via PowerShell (conexão, uploads, execução de scripts), acesse:

[Lista de comandos PowerShell para EC2 e S3](power_shell_comandos.md)
