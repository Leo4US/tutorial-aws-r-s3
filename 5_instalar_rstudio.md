## 5. Instalar o R e o RStudio Server
```bash
sudo apt update
sudo apt install r-base -y

wget https://download2.rstudio.org/server/jammy/amd64/rstudio-server-2023.06.2-561-amd64.deb
sudo apt install ./rstudio-server-2023.06.2-561-amd64.deb
```

- Acessar no navegador: http://SEU-IP:8787
- Utilizar o usuário padrão da instância ou criar um novo com `sudo adduser nome_usuario`

---