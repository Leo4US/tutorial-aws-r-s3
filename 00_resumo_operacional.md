# Resumo Operacional: Criar conta, configurar EC2 e operar com R

Este resumo apresenta os passos essenciais para iniciar rapidamente no uso da AWS com R, sem detalhes extensos.

---

## 1. Criar conta na AWS
- Acessar: https://aws.amazon.com/pt/
- Criar conta com e-mail e cartão de crédito internacional
- Acessar o console: https://console.aws.amazon.com/

## 2. Criar instância EC2
- Navegar até EC2
- Selecionar "Executar instância"
- AMI: Ubuntu Server 22.04
- Tipo: t2.micro (Free Tier)
- Criar e baixar chave `.pem`
- Liberar porta 22 (SSH) e 8787 (RStudio, opcional)
- Iniciar instância e copiar o IP público

## 3. Acessar via terminal
```bash
ssh -i chave.pem ubuntu@SEU-IP
```

## 4. Instalar R na instância
```bash
sudo apt update
sudo apt install r-base -y
```

## 5. (Opcional) Instalar RStudio Server
```bash
wget https://download2.rstudio.org/server/jammy/amd64/rstudio-server-2023.06.2-561-amd64.deb
sudo apt install ./rstudio-server-2023.06.2-561-amd64.deb
```
Acessar via navegador: `http://SEU-IP:8787`

## 6. Configurar AWS CLI
```bash
sudo apt install awscli
aws configure
```

## 7. Criar bucket S3
- Acessar: https://s3.console.aws.amazon.com/s3/
- Criar bucket com nome único
- Desbloquear acesso público se necessário

## 8. Subir e baixar arquivos
```bash
aws s3 cp arquivo.csv s3://nome-do-bucket/
aws s3 cp s3://nome-do-bucket/arquivo.csv .
```

---

Este resumo é útil para revisar os comandos principais ou compartilhar rapidamente com colegas.