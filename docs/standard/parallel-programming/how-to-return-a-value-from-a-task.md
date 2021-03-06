---
title: Практическое руководство. Возврат значения из задачи
description: Узнайте, как использовать тип System.Threading.Tasks.Task<TResult> для возврата значения из свойства Result в .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: c7a4a683545c9ef0448d9cdce769aae79215aecf
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825615"
---
# <a name="how-to-return-a-value-from-a-task"></a>Практическое руководство. Возврат значения из задачи
В этом примере показано, как использовать тип <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> для возврата значения из свойства <xref:System.Threading.Tasks.Task%601.Result%2A>. Здесь требуется, чтобы каталог C:\Users\Public\Pictures\Sample Pictures\ существовал и содержал файлы.  
  
## <a name="example"></a>Пример  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 Свойство <xref:System.Threading.Tasks.Task%601.Result%2A> блокирует вызывающий поток до завершения задачи.  
  
 Дополнительные сведения о том, как передать результат одной <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> в задачу продолжения, см. в руководстве по [созданию цепочки задач с помощью задач продолжения](chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>См. также

- [Асинхронное программирование на основе задач](task-based-asynchronous-programming.md)
- [Лямбда-выражения в PLINQ и TPL](lambda-expressions-in-plinq-and-tpl.md)
