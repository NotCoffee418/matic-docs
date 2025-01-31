---
id: port-management
title: Техническая инфраструктура для нодов
sidebar_label: Technical Infrastructure For Nodes
description: Список портов по умолчанию, используемых в Polygon нодами
keywords:
  - docs
  - polygon
  - matic
  - port
  - port management
  - infrastructure
  - default ports
image: https://wiki.polygon.technology/img/polygon-wiki.png
---

Ниже представлен список портов по умолчанию, которые используются в нодах Polygon:

## Bor {#bor}

| ﻿Название | Порт | Теги | Описание |
|------------------------|-------|---------------------------|----------------------------------------------------------------------------------------------------------------|
| Порт прослушивания сети | 30303 | публичный | Порт прослушивания сети. Bor использует этот порт для подключения к одноранговым узлам и синхронизации. |
| Сервер удаленного вызова процедур | 8545 | может быть публичным, внутренний | Порт удаленного вызова процедур служит для отправки транзакций и получения данных из уровня Bor. Heimdall использует этот порт, чтобы получать заголовки Bor для чекпоинтов. |
| Сервер WS | 8546 | может быть публичным, внутренний | Порт WebSocket. |
| Сервер Graphql | 8547 | может быть публичным, внутренний | Порт Graphql. |
| Сервер Prometheus | 9091 | может быть публичным, контрольный | API сервера Prometheus в качестве источника данных в Grafana. Его можно сопоставить с 80/443 с помощью обратного прокси-сервера nginx. |
| Сервер Grafana | 3001 | может быть публичным, контрольный | Веб-сервер Grafana. Его можно сопоставить с 80/443 с помощью обратного прокси-сервера nginx. |
| Сервер Pprof | 7071 | внутренний, контрольный | Сервер Pprof для получения метрик из уровня Bor. |
| Обнаружение UDP | 30301 | может быть публичным, внутренний | Порт загрузки узлов по умолчанию (для обнаружения одноранговых узлов). |

## Heimdall {#heimdall}

| ﻿Название | Порт | Теги | Описание |
|------------------------|-------|---------------------------|----------------------------------------------------------------------------------------------------------------|
| Порт прослушивания сети | 30303 | публичный | Порт прослушивания сети. Bor использует этот порт для подключения к одноранговым узлам и синхронизации. |
| Сервер удаленного вызова процедур | 8545 | может быть публичным, внутренний | Порт удаленного вызова процедур служит для отправки транзакций и получения данных из уровня Bor. Heimdall использует этот порт, чтобы получать заголовки Bor для чекпоинтов. |
| Сервер WS | 8546 | может быть публичным, внутренний | Порт WebSocket. |
| Сервер Graphql | 8547 | может быть публичным, внутренний | Порт Graphql. |
| Сервер Prometheus | 9091 | может быть публичным, контрольный | API сервера Prometheus в качестве источника данных в Grafana. Его можно сопоставить с 80/443 с помощью обратного прокси-сервера nginx. |
| Сервер Grafana | 3001 | может быть публичным, контрольный | Веб-сервер Grafana. Его можно сопоставить с 80/443 с помощью обратного прокси-сервера nginx. |
| Сервер Pprof | 7071 | внутренний, контрольный | Сервер Pprof для получения метрик из уровня Bor. |
| Обнаружение UDP | 30301 | может быть публичным, внутренний | Порт загрузки узлов по умолчанию (для обнаружения одноранговых узлов). |