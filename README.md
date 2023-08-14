# Защита сети - Александр Шевцов

Запускаем nmap сканирования ноды с suricata и fail2ban
![image](https://github.com/aztecprod/Protect-network/assets/25949605/9b2cfac7-b367-4765-bf12-952019d6decf)


Логи Suricata:
```
08/14/2023-19:21:23.460617  [**] [1:2013409:3] ET POLICY Outbound MSSQL Connection to Non-Standard Port - Likely Malware [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.0.109:42830 -> 192.168.0.108:3000
08/14/2023-19:21:28.465146  [**] [1:2013409:3] ET POLICY Outbound MSSQL Connection to Non-Standard Port - Likely Malware [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.0.109:42830 -> 192.168.0.108:3000
08/14/2023-19:21:33.469408  [**] [1:2034730:1] ET POLICY GIOP/IIOP Request Outbound [**] [Classification: Potential Corporate Privacy Violation] [Priority: 1] {TCP} 192.168.0.109:38124 -> 192.168.0.108:3000
08/14/2023-19:21:38.473021  [**] [1:2034730:1] ET POLICY GIOP/IIOP Request Outbound [**] [Classification: Potential Corporate Privacy Violation] [Priority: 1] {TCP} 192.168.0.109:38124 -> 192.168.0.108:3000
08/14/2023-19:21:38.480795  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53538 -> 192.168.0.108:80
08/14/2023-19:21:38.480795  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53538 -> 192.168.0.108:80
08/14/2023-19:21:38.480979  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53548 -> 192.168.0.108:80
08/14/2023-19:21:38.480979  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53548 -> 192.168.0.108:80
08/14/2023-19:21:38.482441  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52694 -> 192.168.0.108:9090
08/14/2023-19:21:38.482441  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52694 -> 192.168.0.108:9090
08/14/2023-19:21:38.482611  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52686 -> 192.168.0.108:9090
08/14/2023-19:21:38.482611  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52686 -> 192.168.0.108:9090
08/14/2023-19:21:38.581401  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53570 -> 192.168.0.108:80
08/14/2023-19:21:38.581401  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:53570 -> 192.168.0.108:80
08/14/2023-19:21:38.582035  [**] [1:2009358:6] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52706 -> 192.168.0.108:9090
08/14/2023-19:21:38.582035  [**] [1:2024364:4] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.0.109:52706 -> 192.168.0.108:9090
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
