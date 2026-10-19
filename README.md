# CRM System

CRM для автоматизации продаж и управления товарными запасами предприятия.

## Структура

- `frontend/` — React, TypeScript, Vite, SCSS; здесь находятся существующие исходники фронтенда.
- `backend/` — NestJS, TypeScript, REST API, Prisma.
- `compose.yaml` — PostgreSQL для локальной разработки.
- `pnpm-workspace.yaml` — общий workspace, один lock-файл в корне.

## Запуск

Требуются Node.js 24, pnpm и Docker Compose для базы данных.

```bash
pnpm install
cp backend/.env.example backend/.env
docker compose up -d
pnpm dev
```

Фронтенд: http://localhost:5173. Бэкенд: http://localhost:3000/api.
Документация: http://localhost:3000/api/docs.
Vite перенаправляет запросы `/api` на бэкенд.

```bash
pnpm build
pnpm lint
pnpm test:backend
```

## База и авторизация

Конфигурация Prisma подготовлена. Модели, миграции, подключение Prisma к модулям
и авторизация будут реализованы при разработке предметных модулей.
Пакеты сессий и хеширования установлены; сам вход пользователей ещё не реализован.
После добавления моделей: `pnpm --filter @crm/backend db:generate` и
`pnpm --filter @crm/backend db:migrate`.

Стили пишутся вручную в SCSS; Tailwind и shadcn/ui не используются.
