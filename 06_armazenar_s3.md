## 6. Armazenar arquivos no Amazon S3
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
