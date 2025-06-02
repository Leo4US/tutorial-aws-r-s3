# Resumo Operacional: criar conta, configurar EC2 e operar com R

Passos para iniciar no uso da AWS com R, sem detalhes extensos.

---

## 1. Criar conta na AWS
- Acessar: https://aws.amazon.com/pt/
- Se não funcionar ou ficar perdido/a vai direto > https://us-east-2.signin.aws.amazon.com/oauth?backwards_compatible=false&iam_user=true&scope=openid&response_type=code&code_challenge_method=SHA-256&redirect_uri=https%3A%2F%2Fus-east-2.console.aws.amazon.com%2Fconsole%2Fhome%3FhashArgs%3D%2523%26isauthcode%3Dtrue%26nc2%3Dh_m_mc%26state%3DhashArgsFromTB_us-east-2_843b0e717a3e1b64%26useDefaultRegion%3Dtrue&client_id=arn%3Aaws%3Asignin%3A%3A%3Aconsole%2Fcanvas&code_challenge=MYNknXvwuhYHzCRZx1KFeUeSY4Ri2eMKpTy8CSkwv4g
- Criar conta com e-mail e cartão de crédito internacional. Até o roxinho serve! Hehe!
- Acessar o console: https://console.aws.amazon.com/

## 2. Criar instância EC2
- Navegar até EC2
- Selecionar "Executar instância"
- AMI: Ubuntu Server 22.04
- Tipo: t2.micro (Free Tier) ou mais potentes
- Criar e baixar chave `.pem`
- Liberar porta 22 (SSH) e 8787 (RStudio, opcional). Obs: não fiz esta etapa. Dei comandos direto do powershell e outra: foi Py.
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
- Criar bucket
- Acesso público?

## 8. Subir e baixar arquivos
```bash
aws s3 cp arquivo.csv s3://nome-do-bucket/
aws s3 cp s3://nome-do-bucket/arquivo.csv .
```
