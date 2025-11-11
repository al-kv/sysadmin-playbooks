# 🖥️ Linux Process & System Diagnostics Playbook

README-шпаргалка: **как быстро понять, что сервер жив и не перегружен**.  
Включает команды для проверки CPU, памяти, дисков и логов.

---

## ✨ Описание

Этот playbook помогает системному администратору:
- 📊 Проверить загрузку CPU и uptime.
- 🧠 Диагностировать использование памяти.
- 💾 Оценить состояние дисков и I/O.
- 📜 Просмотреть системные логи.

---

## ⚙️ Setup

Установите утилиты:

```bash
sudo apt install htop sysstat iotop


htop — удобный мониторинг процессов.

sysstat — включает vmstat, iostat.

iotop — мониторинг дисковых операций.

🚀 QuickStart

uptime             # Проверка времени работы и средней загрузки
top                # Общая загрузка CPU и процессов
htop               # Более удобный мониторинг
free -h            # Использование памяти
vmstat 1 5         # Статистика памяти и процессов
df -h              # Использование дисков
du -sh /var/log    # Размер каталога
iotop              # Мониторинг дисковых операций
journalctl -xe     # Системные логи
dmesg | tail -20   # Последние сообщения ядра

📊 Checklist

Что проверяем	   Команды

CPU	            top, htop, uptime
Memory	            free -h, vmstat
Disk usage	    df -h, du -sh <dir>
Disk I/O	    iotop, iostat
Logs	             journalctl -xe, dmesg

🛠 Algorithm (от простого к сложному)

Uptime → uptime (сервер работает, нагрузка нормальная?).

CPU → top / htop (нет ли процессов с 100% CPU?).

Memory → free -h, vmstat (есть ли свободная память?).

Disk usage → df -h, du -sh (нет ли переполненных разделов?).

Disk I/O → iotop (нет ли процессов, перегружающих диск?).

Logs → journalctl -xe, dmesg (ошибки ядра, служб?).

🛠 Algorithm (от простого к сложному)

1 - Uptime → uptime (сервер работает, нагрузка нормальная?).

2 - CPU → top / htop (нет ли процессов с 100% CPU?).

3 - Memory → free -h, vmstat (есть ли свободная память?).

4 - Disk usage → df -h, du -sh (нет ли переполненных разделов?).

5 - Disk I/O → iotop (нет ли процессов, перегружающих диск?).

6 - Logs → journalctl -xe, dmesg (ошибки ядра, служб?).


🧩 Usage — реальные кейсы

1. Сервер перегружен по CPU

top
htop

✅ Найти процесс с высоким CPU. ❌ Если процесс "завис" → перезапустить или убить (kill -9 <pid>).


2. Мало памяти

free -h
vmstat 1 5

✅ Проверить swap. ❌ Если памяти нет → оптимизировать процессы, добавить swap.

3. Диск заполнен

df -h
du -sh /var/log

✅ Найти переполненный раздел. ❌ Очистить логи, временные файлы.

4. Служба зависла

systemctl status <service>
journalctl -u <service>

✅ Проверить логи. ❌ Перезапустить службу.

📈 Visual Schemes

Flowchart: CPU → Memory → Disk → Logs.

Playbook: "Если нагрузка высокая → ищем процесс → проверяем память → проверяем диск → смотрим логи".

📜 License

Свободно использовать и адаптировать для учебных и рабочих целей.





