# Домашнее задание к занятию «Защита сети» - `Смирнов Максим`

### Задание 1

Проведите разведку системы и определите, какие сетевые службы запущены на защищаемой системе:

```
sudo nmap -sA < ip-адрес >
sudo nmap -sT < ip-адрес >
sudo nmap -sS < ip-адрес >
sudo nmap -sV < ip-адрес >
```

В качестве ответа пришлите события, которые попали в логи Suricata и Fail2Ban

***

В качестве атакуемой машины использовался базовый Debian, в нем были закрыты все порты. Как результат сканирования:
- Suricata видит подключения и срабатывает установленное правило про предупреждение о сканировании
- Fail2ban бездействует, поскольку атаки на ssh инфраструктуру нет
- nmap не нашел открытых портов - причина объяснена выше - Debian базовый и ssh служба установлена не была

`Результаты в nmap`

![assign1-logs-nmap.jpg](https://github.com/turboturtle-90/Network-protection/blob/b2a24d1b0889fd090e7f671ae43fda84bb099c17/assign1-logs-nmap.jpg)

`Результаты в Suricata`

![assign1-logs-suricata.jpg](https://github.com/turboturtle-90/Network-protection/blob/b2a24d1b0889fd090e7f671ae43fda84bb099c17/assign1-logs-suricata.jpg)

`Результаты в Fail2Ban`

![assign1-logs-fail2ban.jpg](https://github.com/turboturtle-90/Network-protection/blob/b2a24d1b0889fd090e7f671ae43fda84bb099c17/assign1-logs-fail2ban.jpg)



***
***

### Задание 2

Проведите атаку на подбор пароля для службы SSH:

```
hydra -L users.txt -P pass.txt < ip-адрес > ssh
```

В качестве ответа пришлите события, которые попали в логи Suricata и Fail2Ban, прокомментируйте результат.

***

При атаке Suricata видит признаки сканирования и информирует об этом. Fail2Ban ведет себя как и ожидается: после 5 попыток подбора пароля добавляет атакующий ip в бан.

`Результаты в Suricata`

![assign2-logs-suricata-.jpg](https://github.com/turboturtle-90/Network-protection/blob/18fc1ceee3002a7c0f1ee315d759cc0168a186d7/assign2-logs-suricata-.jpg)


`Результаты в Fail2Ban`

![assign2-logs-fail2ban-.jpg](https://github.com/turboturtle-90/Network-protection/blob/18fc1ceee3002a7c0f1ee315d759cc0168a186d7/assign2-logs-fail2ban-.jpg)



---
