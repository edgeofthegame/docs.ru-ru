---
title: Количество зафиксированных операций с поддержкой транзакций в секунду
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 047640e9b5cc22f2d443832fb7bd5afd47aef5be
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550642"
---
# <a name="transacted-operations-committed-per-second"></a>Количество зафиксированных операций с поддержкой транзакций в секунду
Имя счетчика: Количество зафиксированных операций с поддержкой транзакций в секунду.  
  
## <a name="description"></a>Описание  
 Количество транзакционных операций, зафиксированных в этой службе за секунду.  
  
 Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
