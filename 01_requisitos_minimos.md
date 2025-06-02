# Tutorial: Rodar R na Nuvem com AWS EC2 + Armazenar Arquivos no S3
## 1. Requisitos mínimos para utilizar EC2 e S3 com R

Para utilizar os serviços EC2 (computação) e S3 (armazenamento) da AWS com scripts em R, não é necessário instalar interfaces gráficas como o RStudio Server. Abaixo estão os componentes essenciais:

### EC2 (Elastic Compute Cloud)
- Conta ativa na AWS
- Instância EC2 com sistema operacional (ex: Ubuntu)
- Chave de acesso `.pem` para autenticação via SSH
- Terminal com suporte a SSH (PowerShell, Linux, macOS)
- R instalado na instância (`sudo apt install r-base`)
- (Opcional) RStudio Server, para acessar R via navegador

### S3 (Simple Storage Service)
- Bucket criado na conta AWS
- AWS CLI instalado e configurado (`aws configure`)
- Permissões para listar, subir e baixar arquivos no bucket
- (Opcional) Biblioteca `aws.s3` instalada no R

Com esses componentes, é possível rodar scripts R diretamente no terminal da EC2 e interagir com arquivos armazenados no S3, sem necessidade de interface gráfica.

Este guia destina-se a orientar iniciantes no uso de recursos da Amazon Web Services (AWS) para:

- Rodar scripts em R na nuvem (via EC2)
- Armazenar e acessar arquivos na nuvem (via S3)

---
