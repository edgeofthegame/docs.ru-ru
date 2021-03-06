---
title: Типизированные наборы данных
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 4648d49b1d7419d61a3a000404f42e0d02d25786
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198452"
---
# <a name="typed-datasets"></a>Типизированные наборы данных

Наряду с доступом к значениям с поздним связыванием через слабо типизированные переменные, в объекте <xref:System.Data.DataSet> предоставляется доступ к данным на основе принципа строгой типизации. Доступ к таблицам и столбцам, которые являются частью **набора данных** , можно получить с помощью понятных имен и строго типизированных переменных.  
  
 Типизированный **набор данных** — это класс, производный от **набора данных**. Таким образом, он наследует все методы, события и свойства **набора данных**. Кроме того, типизированный **набор данных** предоставляет строго типизированные методы, события и свойства. Это означает, что к таблицам и столбцам можно обращаться путем указания имен вместо использования методов на основе коллекций. Помимо улучшенной удобочитаемости кода, типизированный **набор данных** также позволяет редактору кода Visual Studio .NET автоматически завершать строки по мере ввода.  
  
 Кроме того, строго типизированный **набор данных** предоставляет доступ к значениям в качестве правильного типа во время компиляции. При использовании строго типизированного **набора данных**ошибки несоответствия типов перехватываются при компиляции кода, а не во время выполнения.  
  
## <a name="in-this-section"></a>в этом разделе  

 [Создание строго типизированных наборов данных](generating-strongly-typed-datasets.md)  
 Описывает создание и использование строго типизированного **набора данных**.  
  
 [Создание примечаний к типизированным наборам данных](annotating-typed-datasets.md)  
 Описывает, как закомментировать схему XSD, используемую для создания строго типизированного **набора данных**, чтобы предоставить понятные имена элементам **набора данных** без изменения базовой схемы.  
  
## <a name="see-also"></a>См. также раздел

- [Наборы данных, таблицы данных и объекты DataView](index.md)
- [Общие сведения об ADO.NET](../ado-net-overview.md)
