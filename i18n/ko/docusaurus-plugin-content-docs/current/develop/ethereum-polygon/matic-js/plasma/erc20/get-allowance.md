---
id: get-allowance
title: getAllowance
keywords:
- 'plasma client, erc20, getAllowance, polygon, sdk'
description: '사용자에게 승인된 금액을 가져옵니다.'
---

`getAllowance` 메서드를 사용해 사용자에게 승인된 금액을 가져올 수 있습니다.

```
const erc20Token = plasmaClient.erc20(<token address>, true);

const balance = await erc20Token.getAllowance(<userAddress>);
```
