# 🐳 Docker & Containers Troubleshooting Playbook

README-шпаргалка: **что делать, если контейнер не стартует**.  
Включает команды для проверки состояния контейнеров, сетей и очистки ресурсов.

---

## ✨ Описание

Этот playbook помогает DevOps-инженеру:
- 📦 Проверить состояние контейнеров.
- 🌐 Диагностировать сетевые проблемы.
- 🧹 Очистить ресурсы и освободить место.
- 🔍 Найти причины зависания контейнера.

---

## ⚙️ Setup

Установите Docker и утилиты:

```bash
sudo apt install docker.io
sudo systemctl enable docker
sudo systemctl start docker


🚀 QuickStart

docker ps                # Список запущенных контейнеров
docker logs <id>         # Логи контейнера
docker inspect <id>      # Подробная информация
docker network ls        # Список сетей
docker system prune      # Очистка ресурсов


📊 Checklist

Что проверяем	    Команды
Контейнеры	    docker ps, docker logs <id>
Сеть	            docker network ls, docker inspect <id>
Ресурсы	            docker system df, docker system prune
Службы Docker	    systemctl status docker

🛠 Algorithm (от простого к сложному)

1 - Проверить контейнеры → docker ps.

2 - Посмотреть логи → docker logs <id>.

3 - Проверить сеть → docker network ls, docker inspect <id>.

4 - Очистить ресурсы → docker system prune.

5 - Проверить Docker daemon → systemctl status docker.

🧩 Usage — реальные кейсы

1. Контейнер не стартует

docker ps -a
docker logs <id>

✅ Найти ошибку в логах. ❌ Если проблема в образе → пересобрать или обновить.

2. Нет сети

docker network ls
docker inspect <id>

✅ Проверить, что контейнер подключён к сети. ❌ Если нет → docker network connect <network> <id>.

3. Контейнер завис

docker ps
docker stop <id>
docker restart <id>

✅ Перезапустить контейнер. ❌ Если не помогает → удалить и пересоздать.

4. Очистка ресурсов

docker system df
docker system prune -a

✅ Освободить место. ❌ Если нужно сохранить образы → использовать выборочную очистку.

📈 Visual Schemes

Flowchart: "Контейнер не стартует → логи → сеть → ресурсы → daemon".

Playbook: "Если контейнер завис → перезапуск → пересоздание".

📜 License

Свободно использовать и адаптировать для учебных и рабочих целей.






