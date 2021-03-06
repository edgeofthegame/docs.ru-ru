---
title: Константа должна быть величиной внутреннего или перечислимого типа, а не классом, структурой, параметром типа или массивом
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: e820287f0ddf462b30867d90501f7d730c9c6739
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163159"
---
# <a name="bc30424-constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>BC30424: константы должны иметь встроенный или перечислимый тип, а не класс, структуру, параметр типа или тип массива

Предпринята попытка объявить константу как класс, структуру или тип массива или как параметр типа, определенный содержащим универсальным типом.

 Константы должны иметь встроенный тип ( `Boolean` , `Byte` ,, `Date` , `Decimal` `Double` , `Integer` , `Long` ,,,,,,, `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` или `UShort` ) или тип, `Enum` основанный на одном из целочисленных типов.

 **Идентификатор ошибки:** BC30424

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Объявите константу как внутренний или `Enum` тип.

2. Константа также может быть специальным значением, таким как `True` , `False` или `Nothing` . Компилятор считает эти предопределенные значения соответствующим внутренним типом.

## <a name="see-also"></a>См. также

- [Константы и перечисления](../constants-and-enumerations.md)
- [Типы данных](../../programming-guide/language-features/data-types/index.md)
- [Типы данных](../data-types/index.md)
