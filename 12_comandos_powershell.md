Alguns comandos que usei no terminal para trabalhar com EC2 e S3. Fui compilando como um dicionário kkk

---

ssh -i "C:\CAMINHO\minha_chave.pem" ubuntu@IP_DA_INSTANCIA  
# Acesso à instância EC2

cd C:\CAMINHO  
# Entrar na pasta onde está a chave .pem

sudo apt update  
sudo apt install r-base -y  
sudo apt install awscli -y  
# Instalar pacotes dentro da EC2 (via SSH)

wget https://download2.rstudio.org/server/jammy/amd64/rstudio-server-2023.06.2-561-amd64.deb  
sudo apt install ./rstudio-server-2023.06.2-561-amd64.deb  
# Instalar RStudio Server (opcional)

aws configure  
# Configurar acesso à AWS CLI

aws s3 cp "C:\CAMINHO\meuarquivo.csv" s3://meu-bucket/  
# Subir arquivo para o S3

aws s3 cp s3://meu-bucket/meuarquivo.csv "C:\CAMINHO"  
# Baixar arquivo do S3

aws s3 ls  
# Listar todos os buckets

aws s3 ls s3://meu-bucket/  
# Ver arquivos dentro de um bucket

aws s3 sync "C:\minha_pasta" s3://meu-bucket/  
# Sincronizar uma pasta local com o bucket

---

Alguns comandos entre meu pc e a AWS.
