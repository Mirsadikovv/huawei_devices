# Все эндпоинты Huawei SMC & RSE API

## SMC 23.0 — Conference & Maintenance API  
**Базовый URL**: `https://<SMC_IP>:8443/SMCAPI/rest`

### 1. Аутентификация
- `POST /login` — Вход в систему (возвращает `JSESSIONID`)
- `POST /logout` — Выход

### 2. Управление конференциями
- `POST /conferences` — Создать конференцию
- `GET /conferences/{id}` — Получить данные конференции
- `PUT /conferences/{id}` — Изменить конференцию
- `DELETE /conferences/{id}` — Отменить конференцию
- `GET /conferences` — Поиск конференций (с фильтрами)
- `GET /conferences/earliest` — Найти ближайшую запланированную
- `GET /conferences/token/{id}` — Получить токен конференции
- `GET /conferences/history` — История конференций
- `GET /conferences/mcu` — MCU, используемые в конференции
- `GET /conferences/mcu/resources` — Ресурсы MCU
- `GET /conferences/capabilities` — Возможности конференции
- `GET /conferences/settings` — Настройки конференции

### 3. Участники
- `POST /conferences/{id}/participants` — Добавить участника
- `DELETE /conferences/{id}/participants/{pid}` — Удалить участника
- `GET /conferences/{id}/participants` — Список участников
- `POST /conferences/{id}/control` — Управление участником (mute, video, etc.)
- `POST /conferences/{id}/participants/batch` — Массовое управление
- `POST /conferences/{id}/participants/migrate` — Миграция участников
- `GET /conferences/{id}/participants/preview` — Превью изображения

### 4. Повторяющиеся конференции
- `POST /recurring/conferences` — Создать серию
- `DELETE /recurring/conferences/{id}` — Удалить всю серию
- `PUT /recurring/conferences/{id}` — Изменить всю серию

### 5. Запись и трансляция
- `POST /conferences/{id}/record/start` — Начать запись
- `POST /conferences/{id}/record/stop` — Остановить запись
- `POST /conferences/{id}/broadcast/start` — Начать трансляцию
- `POST /conferences/{id}/broadcast/stop` — Остановить трансляцию

---

## SMC 23.0 — Device & Terminal Management API  
**Базовый URL**: `https://<SMC_IP>:8443/SMCAPI/rest`

### 1. MCU
- `GET /mcu` — Поиск всех MCU
- `POST /mcu` — Добавить MCU
- `POST /mcu/monitor` — Добавить мониторинговый MCU
- `PUT /mcu/{id}` — Обновить MCU
- `PUT /mcu/monitor/{id}` — Обновить мониторинговый MCU
- `GET /mcu/{id}` — Получить один MCU
- `DELETE /mcu/{id}` — Удалить MCU
- `DELETE /mcu/batch` — Удалить пакетно
- `GET /mcu/{id}/config` — Получить конфигурацию
- `POST /mcu/{id}/config/deliver` — Отправить конфигурацию
- `GET /mcu/testConnection` — Проверить соединение
- `GET /mcu/testConnection/v20` — (Совместимо с 20.1)
- `GET /mcu/{id}/performance` — Производительность
- `GET /mcu/template` — Скачать шаблон импорта
- `POST /mcu/import` — Импорт MCU пакетно
- `GET /mcu/count` — Количество MCU
- `POST /mcu/status/subscribe` — Подписка на статус
- `POST /mcu/status/unsubscribe` — Отписка
- `GET /mcu/monitor/files` — Экспорт файлов мониторинга
- `POST /mcu/resources/clear` — Очистить ресурсы
- `GET /mcu/resources/usage` — Использование ресурсов
- `GET /mcu/resources/usage/time` — По времени

### 2. SC (Switch Center)
- `GET /sc/zones` — Зоны
- `POST /sc/zones` — Добавить зону
- `GET /sc/routes` — Правила маршрутизации
- `POST /sc/certificates` — Загрузка сертификатов

### 3. RSE (в SMC)
- `GET /rse/connections` — Статус подключения
- `POST /rse/connections/change` — Сменить подключение

### 4. Терминалы
- `GET /terminals` — Список терминалов
- `GET /terminals/groups` — Группы
- `POST /terminals/{id}/logs/upload` — Загрузить логи
- `GET /terminals/{id}/logs/download` — Скачать логи
- `POST /terminals/deployment` — Развертывание задач
- `POST /terminals/materials` — Рассылка материалов
- `POST /terminals/programs` — Рассылка программ
- `POST /terminals/apps` — Установка приложений

---

## RSE8800A 21.0 API  
**Базовый URL**: `https://<RSE_IP>:8443/api`

### 1. Аутентификация и доступ
- `GET /guestInfo?ticket=<CTI_TICKET>` — Получить гостевые данные
- `POST /login` — Вход (user + password)
- `POST /logout` — Выход

### 2. Управление ресурсами
- `POST /bandwidth/apply` — Запросить пропускную способность
- `POST /bandwidth/release` — Освободить пропускную способность

### 3. Записи и трансляции
- `GET /playback/info` — Информация о воспроизведении
- `GET /live` — Запрос live-трансляции
- `GET /vod` — Запрос VOD
- `GET /recording/{confId}/segment/{n}` — Скачать сегмент записи
- `GET /minutes/{confId}` — Скачать протокол конференции

### 4. Интеграция с CTI
- `GET /cti/download` — Интерфейс для CTI (машинный доступ к записям)

---

> **Примечание**: Все эндпоинты требуют HTTPS и аутентификации (`JSESSIONID` для SMC, `sessionID` для RSE).  
> Используйте `Content-Type: application/json` и передавайте `Cookie` или `sessionID` в заголовках.