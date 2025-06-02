## 10. Observações finais
- Lembrar de parar a instância quando não estiver utilizando, para evitar cobranças:

```bash
aws ec2 stop-instances --instance-ids i-xxxxxxxxxxxx
```

- Recomendar criar scripts automatizados e configurar o agendamento de tarefas via `cron`.