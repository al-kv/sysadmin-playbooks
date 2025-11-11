# 🌐 Networking Advanced (VLAN, VPN, Tunnels) Playbook

README-шпаргалка: **быстрый старт по продвинутым сетевым фичам**.  
Включает команды для проверки VLAN, настройки туннелей и диагностики VPN.

---

## ✨ Описание

Этот playbook помогает системному администратору:
- 🧩 Проверить VLAN и сетевые интерфейсы.
- 🔗 Настроить GRE-туннели и проверить их работу.
- 🔐 Диагностировать VPN-соединения.
- 📡 Быстро реагировать на сетевые инциденты.

---

## ⚙️ Setup

Установите утилиты:

```bash
sudo apt install iproute2 openvpn tcpdump


iproute2 — работа с интерфейсами, VLAN, туннелями.

openvpn — VPN-клиент/сервер.

tcpdump — анализ пакетов.

🚀 QuickStart

ip -d link show          # Проверка VLAN
ip tunnel add gre1 mode gre remote 192.168.1.1 local 192.168.1.2 ttl 255
ip link set gre1 up
systemctl status openvpn # Проверка VPN
tcpdump -i eth0          # Анализ трафика

📊 Checklist

Что проверяем	      Команды

VLAN	               ip -d link show, tcpdump -i eth0 -e
GRE Tunnel             ip tunnel add, ip link set, ip addr show
VPN                    systemctl status openvpn, journalctl -u openvpn
Трафик                 tcpdump, ping, curl


🛠 Algorithm (от простого к сложному)

1 - Проверить VLAN → ip -d link show.

2 - Проверить туннель → ip tunnel add, ip link set gre1 up.

3 - Проверить VPN → systemctl status openvpn.

4 - Анализировать трафик → tcpdump -i eth0.

5 - Проверить firewall → iptables -L -n -v.

🧩 Usage — реальные кейсы

1. Нет доступа через VPN
systemctl status openvpn
journalctl -u openvpn

✅ Проверить, что VPN-сервис активен. ❌ Если нет → перезапустить, проверить конфиг.

2. Не работает VLAN
ip -d link show
tcpdump -i eth0 -e

✅ Проверить наличие VLAN-тегов. ❌ Если нет → проверить конфигурацию коммутатора.

3. Туннель не поднимается
ip tunnel add gre1 mode gre remote 192.168.1.1 local 192.168.1.2 ttl 255
ip link set gre1 up
ip addr show gre1

✅ Интерфейс поднят, есть IP. ❌ Если нет → проверить маршруты и firewall.

📈 Visual Schemes
Flowchart: VLAN → Tunnel → VPN → Traffic.

Playbook: "Если VPN не работает → проверяем сервис → логи → маршруты".

📜 License
Свободно использовать и адаптировать для учебных и рабочих целей.





