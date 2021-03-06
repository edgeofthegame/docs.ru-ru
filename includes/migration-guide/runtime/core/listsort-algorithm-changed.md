---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497413"
---
### <a name="listsort-algorithm-changed"></a>Изменен алгоритм List.Sort

#### <a name="details"></a>Подробнее

Начиная с версии .NET Framework 4.5, алгоритм сортировки <xref:System.Collections.Generic.List%601?displayProperty=fullName> был изменен и реализует интроспективную сортировку вместо быстрой. Сортировка <xref:System.Collections.Generic.List%601?displayProperty=fullName> никогда не была стабильной, однако это изменение может привести к потере стабильности при сортировке в различных других сценариях. Это означает, что эквивалентные элементы могут сортироваться в разном порядке при последовательных вызовах API.

#### <a name="suggestion"></a>Предложение

Поскольку старый алгоритм сортировки также был нестабилен (в несколько другом плане), не следует использовать код, который зависит от постоянства порядка сортировки эквивалентных элементов. Если в коде присутствовала такая зависимость и он ранее выполнялся без ошибок, его следует обновить для использования компаратора, который будет осуществлять детерминированную сортировку элементов в необходимом порядке.

| name    | Значение       |
|:--------|:------------|
| Область   |Прозрачный|
|Version|4.5|
|Type|Среда выполнения|

#### <a name="affected-apis"></a>Затронутые API

- <xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Generic.List`1.Sort``
- ``M:System.Collections.Generic.List`1.Sort(System.Collections.Generic.IComparer{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Comparison{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{`0})``

-->
