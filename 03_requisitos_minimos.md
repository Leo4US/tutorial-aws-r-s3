# Rodar R na Nuvem com AWS EC2 + Armazenar Arquivos no S3
## 1. Requisitos mínimos para utilizar EC2 e S3 com R

Não precisa de interface para usar os serviços AWS > EC2 (computação/processamento) e S3 (armazenamento).

### EC2 (Elastic Compute Cloud)
- Conta ativa na AWS
- Instância EC2 com sistema operacional
- Chave de acesso `.pem` para autenticação via SSH
- Terminal com suporte a SSH (PowerShell, Linux, macOS)
- R instalado na instância (comando > `sudo apt install r-base`)
- É opcional o RStudio Server para acessar R via navegador

### S3 (Simple Storage Service)
- Criar bucket na conta AWS
- AWS CLI instalado e configurado (cmd > `aws configure`)
- Permissões para listar, subir e baixar arquivos no bucket
- (Opcional) Biblioteca `aws.s3` instalada no R

Com isso é possível rodar scripts R diretamente no terminal da EC2 e interagir com arquivos armazenados no S3, sem necessidade de interface gráfica.

Focos:
- Rodar scripts em R na nuvem (via EC2)
- Armazenar e acessar arquivos na nuvem (via S3)
