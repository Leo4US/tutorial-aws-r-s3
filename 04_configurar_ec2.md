## 3. Configurar uma instância EC2
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
