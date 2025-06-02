# Lista de comandos PowerShell para EC2 e S3

Este arquivo contém os comandos que utilizei no PowerShell para operar a AWS EC2 e o armazenamento S3.

---

## 1. Acessar a instância EC2 via SSH

```powershell
ssh -i "C:\CAMINHO\minha_chave.pem" ubuntu@IP_DA_INSTANCIA
```

Obs: a chave `.pem` precisa estar na pasta correta. Pode usar `cd` para navegar.

---

## 2. Instalar pacotes na instância EC2 (depois de logado via SSH)

```bash
sudo apt update
sudo apt install r-base -y
sudo apt install awscli -y
```

---

## 3. Baixar e instalar RStudio Server (opcional)

```bash
wget https://download2.rstudio.org/server/jammy/amd64/rstudio-server-2023.06.2-561-amd64.deb
sudo apt install ./rstudio-server-2023.06.2-561-amd64.deb
```

---

## 4. Configurar AWS CLI

```bash
aws configure
```

Insira:
- Access Key ID
- Secret Access Key
- Região (ex: us-east-2)
- Formato (ex: json)

---

## 5. Comandos para subir e baixar arquivos no S3

### Subir arquivo local para o S3

```powershell
aws s3 cp "C:\CAMINHO\meuarquivo.csv" s3://meu-bucket/
```

### Baixar do S3 para sua máquina local

```powershell
aws s3 cp s3://meu-bucket/meuarquivo.csv "C:\CAMINHO"
```

---

## 6. Comandos úteis adicionais

### Ver lista de buckets

```powershell
aws s3 ls
```

### Ver arquivos dentro de um bucket

```powershell
aws s3 ls s3://meu-bucket/
```

### Sincronizar uma pasta local com um bucket

```powershell
aws s3 sync "C:\minha_pasta" s3://meu-bucket/
```

---

Esses comandos me ajudaram a manter o fluxo entre minha máquina local e os serviços AWS direto do PowerShell.