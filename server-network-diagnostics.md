# 📡 Server Network Diagnostics Playbook

Полный набор инструментов для системного администратора: чеклист по уровням OSI, быстрые команды, алгоритм диагностики, реальные кейсы и визуальные схемы.  
Документ оформлен как README.md — можно использовать в портфолио или репозитории.

---

## ✨ Описание

Этот playbook помогает системному администратору **быстро и последовательно диагностировать сетевые проблемы** на сервере.  
Он объединяет:
- 📊 **Чеклист по уровням OSI**  
- ⚡ **Quick Reference (шпаргалка)**  
- 🛠 **Алгоритм диагностики (от простого к сложному)**  
- 🧩 **Usage — реальные кейсы**  
- 📈 **Визуальные схемы (flowchart и playbook)**  

---

## 📂 Structure

Документ построен логично и последовательно:

1. **Setup** — установка необходимых утилит.  
2. **Quickstart** — быстрые команды для экстренной проверки.  
3. **Checklist (OSI)** — подробный чеклист по уровням.  
4. **Algorithm** — пошаговый сценарий диагностики.  
5. **Quick Reference** — компактная шпаргалка.  
6. **Usage** — реальные кейсы и примеры.  
7. **Visual Schemes** — flowchart и playbook.  
8. **License** — условия использования.  

---

## ⚙️ Setup

Перед использованием убедитесь, что установлены утилиты:

```bash
sudo apt install ethtool iproute2 net-tools dnsutils mtr tcpdump


ethtool — проверка линка и скорости

iproute2 — ip addr, ip route

net-tools — ifconfig, netstat

dnsutils — dig, nslookup

mtr — комбинированный ping+traceroute

tcpdump — анализ пакетов

🚀 Quickstart
ethtool eth0          # Проверка физики
ip addr show          # IP-адрес
ip route show         # Маршруты
ping 8.8.8.8          # Доступность
ss -tuln              # Порты
systemctl status nginx # Службы
dig example.com       # DNS
iptables -L -n -v     # Firewall

📊 Checklist (по уровням OSI)

Уровень OSI	Что проверяем	Команды

Physical	Кабель, линк	ethtool eth0

Data Link	MAC, VLAN	ip link show, arp -a, tcpdump -i eth0 -e

Network	IP, маршруты	ip addr show, ip route show, ping <gateway>

Transport	Порты	ss -tuln, curl -v localhost:<port>

Session	Службы	systemctl status <service>, journalctl -u <service>

Presentation	TLS/SSL	openssl s_client -connect host:443

Application	DNS, веб	dig example.com, curl -I http://example.com

🛠 Algorithm (от простого к сложному)

1 - Физика → ethtool eth0

2 - IP → ip addr show, ip route show

3 - Доступность → ping <gateway>, ping 8.8.8.8

❌ Нет ответа → проверить маршруты

4 - Порты и службы → ss -tuln, systemctl status <service>

❌ Порт закрыт → проверить firewall

5 - DNS → dig example.com, cat /etc/resolv.conf

6 - Логи → journalctl -u <service>, tail -f /var/log/syslog

7 - Дополнительно → MTU, ARP, VLAN


⚡ Quick Reference
Физика: ethtool eth0

IP: ip addr show

Маршруты: ip route show

Доступность: ping 8.8.8.8

Порты: ss -tuln

Службы: systemctl status <service>

DNS: dig example.com

Firewall: iptables -L -n -v

🧩 Usage — реальные кейсы
1. Сервис недоступен

ss -tuln
systemctl status nginx
journalctl -u nginx

✅ Порт открыт, служба активна. ❌ Если нет → проверить firewall, перезапустить сервис.

2. DNS не работает

cat /etc/resolv.conf
dig example.com
ping 8.8.8.8

✅ Корректный nameserver, успешный ответ. ❌ Если нет → заменить DNS-сервер, проверить firewall.

3. Порт закрыт

ss -tuln
iptables -L -n -v
firewall-cmd --list-all

✅ Порт открыт. ❌ Если нет → добавить правило в firewall, проверить SELinux/AppArmor.

4. Нет выхода в интернет

✅ Пинг до шлюза и внешнего IP успешен. ❌ Если нет → проверить маршруты, MTU, VLAN.

📈 Visual Schemes
Flowchart дерева решений (см. приложенные схемы)

Playbook сценарий (см. приложенные схемы)

📜 License
Свободно использовать и адаптировать для учебных и рабочих целей.





