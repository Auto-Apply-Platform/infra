# infra

Инфраструктура для сервисов `website_backend` и `auth_telegram_service`.

## Запуск

```bash
docker compose up --build
```

## HTTPS для Telegram webhook

Telegram требует публичный HTTPS. Задайте домен в переменной:

```bash
export AUTH_TELEGRAM_DOMAIN=auth.example.com
```

И укажите базовый URL для бота:

```env
TELEGRAM_WEBHOOK_PUBLIC_URL=https://auth.example.com
```

Если меняете `TELEGRAM_WEBHOOK_PATH`, обновите путь в `infra/Caddyfile`.

## Локальная разработка (ngrok/localhost.run)

1) Поднимите туннель к порту `80` или `443`:

```bash
ngrok http 80
```

2) Возьмите публичный домен и установите:

```env
TELEGRAM_WEBHOOK_PUBLIC_URL=https://<public-tunnel-domain>
```

3) Перезапустите `auth_telegram_service`, чтобы пересоздать webhook.
