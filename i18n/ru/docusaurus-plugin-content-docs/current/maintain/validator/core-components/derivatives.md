---
id: derivatives
title: Деривативы
description: Делегирование через доли валидатора
keywords:
  - docs
  - polygon
  - matic
  - derivatives
  - delegation
  - shares
slug: derivatives
image: https://wiki.polygon.technology/img/polygon-wiki.png
---

Polygon поддерживает [делегирование](/docs/maintain/glossary#delegator) с помощью долей валидатора. Такая схема позволяет проще распределять награды и масштабировать контракты в Ethereum mainnet без особых вычислений.

Делегаты осуществляют делегирование путем покупки долей ограниченного пула у валидаторов. Каждый валидатор имеет свой собственный токен доли валидатора.

Назовем взаимозаменяемые доли валидатора VATIC для валидатора A. Когда пользователь осуществляет делегирование валидатору A, он получает VATIC с учетом обменного курса пары MATIC-VATIC. По мере накопления средств пользователи смогут вывести больше MATIC за каждый VATIC, так как обменный курс будет улучшаться. Когда средства валидатора сокращаются, пользователи могут вывести меньше MATIC за свои VATIC.

Обращаем внимание, что MATIC — это токен стейкинга. У делегата должны быть токены MATIC для делегирования.

Изначально делегат Г покупает токены из определенного пула валидатора А, когда курс обмена составляет 1 MATIC за 1 VATIC.

Когда валидатор получает награду в виде большего количества токенов MATIC, в пул добавляются новые токены.

Допустим, текущий пул содержит 100 токенов MATIC. В него добавляются 10 токенов MATIC от награды. Поскольку общий объем предложения токенов VATIC не изменился из-за вознаграждения, обменный курс становится 1 MATIC на 0,9 VATIC. Теперь Delegator D получает больше MATIC на ту же сумму, если акции.

## Поток в контракте {#the-flow-in-the-contract}

`buyVoucher`: эта функция присваивается при осуществлении делегирования валидатору. Количество делегируемых средств `_amount` сначала передается менеджеру стейкинга `stakeManager`, который при подтверждении создает доли делегирования с помощью функции `Mint`, используя текущий обменный курс `exchangeRate`.

Обменный курс рассчитывается по следующей формуле:

`ExchangeRate = (totalDelegatedPower + delegatorRewardPool) / totalDelegatorShares`

`sellVoucher`: эта функция вызывается, когда делегат осуществляет отвязку от валидатора. Фактически она запускает процесс продажи ваучеров, которые были куплены во время делегирования. Существует период вывода средств, который учитывается до того, как делегаты смогут получить `claim` свои токены.

`withdrawRewards`: будучи делегатом, вы можете получать награды с помощью функции `withdrawRewards`.

`reStake`: добавление средств в стейкинг устроено следующим образом. Делегат может купить больше долей, используя награды за покупку ваучеров `buyVoucher` или повторный стейкинг `reStake`. Вы можете добавить в стейкинг дополнительные токены или награды, накопленные в качестве делегата, в адрес валидатора. Цель добавления средств в стейкинг `reStaking` заключается в получении более щедрых наград валидатором и делегатом, поскольку валидатор делегата будет иметь более активный стейк.

`unStakeClaimTokens`: после завершения периода вывода средств делегаты, которые продали свои доли, могут получить токены MATIC.

`updateCommissionRate`: эта функция обновляет процент от размера комиссии, которую получает валидатор. См. также статью [Операции с комиссией валидатора](/docs/maintain/validate/validator-commission-operations).

`updateRewards`: когда валидатор получает награду за отправку [чекпоинта](/docs/maintain/glossary#checkpoint-transaction), эта функция используется для распределения наград между валидатором и делегатами.
