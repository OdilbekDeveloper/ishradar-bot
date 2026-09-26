# IshRadar Bot 🔎

Jobs for foreigners in Korea, in one Telegram bot.
Available in Uzbek, English and Russian.

🤖 [@ishradar_bot](https://t.me/ishradar_bot) · 🔒 The code is private

## The problem

Jobs are spread across dozens of Telegram channels, and half of them are spam, duplicates, or posts that don't say which visa they accept.

## Features

| For | What they get |
|---|---|
| 👤 Job seekers | Pick province → city → visa, with live job counts. Save a search and get alerts |
| 🕷 Crawler | Reads approved channels and pulls out city, visa, salary and contact |
| 🔍 Group hunt | Finds new job groups in cities with few jobs. Joins only after admin approval |
| 🛠 Admins | Stats, sources, job editing, reports, ads, broadcast, admin roles |

## How it works

```
Telegram channels → Telethon crawler → parser → PostgreSQL
                                                    ↓
                    public bot + admin bot ← Django + DRF
                                                    ↑
                               Celery + Redis (alerts, stats)
```

## Problems I solved

| Problem | Fix |
|---|---|
| Spam channels | An admin approves every source |
| Slow tasks block the bot | Celery + Redis run them in the background |
| Crawler accounts are sensitive | Sessions are encrypted (Fernet) |
| Hard to tell what broke | Health checks for web, worker, bots and crawler |
| Slow tests | Tests run without Postgres or Redis |

## Stack

Python 3.12 · Django 5 · DRF · PostgreSQL · Redis · Celery · pyTelegramBotAPI · Telethon · Nginx · Docker Compose · Railway
