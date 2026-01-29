# Analysis – LAB 06 Cron Persistence

- Persistencia a nivel de usuario utilizando crontab.
- Script ubicado en ~/.local/bin, una ubicación típica para scripts "ocultos".
- Escritura recurrente en /tmp/.sysupdate.log, indica actividad automatizada.
- Difícil de detectar sin revisar crontabs de usuarios.
- Uso de cron como mecanismo de ejecución periódica sin privilegios.
