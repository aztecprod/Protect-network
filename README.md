# Защита сети - Александр Шевцов

![image](https://github.com/aztecprod/Protect-network/assets/25949605/13685f81-80d3-426f-b597-ad6351e093db)


Запускаем nmap сканирования ноды с suricata и fail2ban

![image](https://github.com/aztecprod/Protect-network/assets/25949605/9b2cfac7-b367-4765-bf12-952019d6decf)


Логи Suricata:

```
08/14/2023-19:21:38.630775  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53578 -> 192.168.0.108:80
08/14/2023-19:21:38.630775  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53578 -> 192.168.0.108:80
08/14/2023-19:21:38.631382  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52712 -> 192.168.0.108:9090
08/14/2023-19:21:38.631382  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52712 -> 192.168.0.108:9090
08/14/2023-19:22:27.203728  [**] [1:2260002:1] SURICATA Applayer Detect protocol only one direction [**] [Classification: Generic Protocol Command Decode] [Priority: 3] {TCP} 192.168.0.108:9090 -> 192.168.0.109:52674
08/14/2023-19:22:27.203918  [**] [1:2260002:1] SURICATA Applayer Detect protocol only one direction [**] [Classification: Generic Protocol Command Decode] [Priority: 3] {TCP} 192.168.0.108:3000 -> 192.168.0.109:42830
08/14/2023-19:22:27.204016  [**] [1:2260002:1] SURICATA Applayer Detect protocol only one direction [**] [Classification: Generic Protocol Command Decode] [Priority: 3] {TCP} 192.168.0.108:3000 -> 192.168.0.109:38124
08/14/2023-19:22:27.204072  [**] [1:2260002:1] SURICATA Applayer Detect protocol only one direction [**] [Classification: Generic Protocol Command Decode] [Priority: 3] {TCP} 192.168.0.108:3000 -> 192.168.0.109:42832
08/14/2023-19:22:27.204125  [**] [1:2260002:1] SURICATA Applayer Detect protocol only one direction [**] [Classification: Generic Protocol Command Decode] [Priority: 3] {TCP} 192.168.0.108:3000 -> 192.168.0.109:569
08/14/2023-19:22:27.204177  [**] [1:2260002:1] SURICATA Applayer Detect protocol only one direction [**] [Classification: Generic Protocol Command Decode] [Priority: 3] {TCP} 192.168.0.108:3000 -> 192.168.0.109:46418

```

Логи Fail2ban:

```
Aug 14 19:45:57 debian2 sshd[6398]: error: kex_exchange_identification: Connection closed by remote host
Aug 14 19:45:57 debian2 sshd[6398]: Connection closed by 192.168.0.109 port 48988
```

В обоих случаях fail2ban и suricata отреагировали лишь на -sV сканирование.

![image](https://github.com/aztecprod/Protect-network/assets/25949605/1d8abb60-f52a-4b39-8897-f2a8ac6f5f2b)


Проверка работы Hydra при выключенной защиты ssh в Fail2ban:

![image](https://github.com/aztecprod/Protect-network/assets/25949605/53f0ba80-abac-4e1e-9fd9-068ff17077d8)

Попытка взлома при включенной защиты ssh в Fail2ban:

![image](https://github.com/aztecprod/Protect-network/assets/25949605/e3ff926a-b736-46da-a849-824267d70b3b)

Логи Fail2ban:

![image](https://github.com/aztecprod/Protect-network/assets/25949605/9b788e2b-7c4f-416b-9527-9055971e0bdd)

Логи Suricata оказались пусты.
