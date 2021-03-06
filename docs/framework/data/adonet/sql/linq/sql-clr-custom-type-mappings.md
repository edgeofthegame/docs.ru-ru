---
title: Настраиваемые сопоставления типов SQL-CLR
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: 14d7f8409f93a5414a37a8b1c8e172f53478e817
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155709"
---
# <a name="sql-clr-custom-type-mappings"></a>Настраиваемые сопоставления типов SQL-CLR

Сопоставление типов SQL Server и среды CLR автоматически указывается при использовании средства командной строки SQLMetal и реляционного конструктора объектов.  
  
 Если настраиваемое сопоставление не выполняется, эти средства назначают сопоставления типов по умолчанию, как описано в разделе [Сопоставление типов SQL-CLR](sql-clr-type-mapping.md). Если вы хотите сопоставлять типы иначе, чем по умолчанию, необходимо выполнить определенную настройку сопоставления типов.  
  
 При проведении пользовательского сопоставления типов рекомендуется выполнять изменения в промежуточном DBML-файле. После этого настроенный DBML-файл следует применять при создании кода и файлов сопоставления с помощью SQLMetal или реляционного конструктора объектов.  
  
 Как только из кода и файлов сопоставления будет создан экземпляр объекта <xref:System.Data.Linq.DataContext>, метод <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> создаст базу данных на основании указанных сопоставлений. Если в этих сопоставлениях нет указанных атрибутов CLR `type`, будут применяться сопоставления по умолчанию.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Настройка с помощью SQLMetal или реляционного конструктора объектов  

 С помощью SQLMetal и реляционного конструктора объектов можно автоматически создать модель объектов, которая будет включать сведения о сопоставлении типов внутри или вне файла кода. Поскольку эти файлы переписываются средствами SQLMetal и реляционного конструктора объектов при каждом повторном создании сопоставлений, рекомендуемым подходом к указанию пользовательских сопоставлений типов является настройка DBML-файла.  
  
 Чтобы настроить сопоставления типов с помощью SQLMetal или реляционного конструктора объектов, сначала создайте файл DBML. Затем, прежде чем создавать файл кода или файл сопоставления, измените DBML-файл, чтобы идентифицировать желаемые сопоставления типов. При использовании SQLMetal необходимо вручную изменить атрибуты `Type` и `DbType` в DBML-файле, чтобы настроить пользовательские сопоставления типов. При использовании реляционного конструктора объектов изменения можно внести средствами конструктора. Дополнительные сведения об использовании реляционного конструктора O/R см. [в разделе средства LINQ to SQL в Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
> Некоторые сопоставления типов могут приводить к возникновению исключений переполнения или потери данных в ходе преобразования данных в базу данных или из нее. Внимательно изучите матрицу поведения сопоставления типов в [сопоставлении типов SQL-CLR](sql-clr-type-mapping.md) перед внесением каких-либо изменений.  
  
 Чтобы настройки сопоставления типов распознавались средством SQLMetal или реляционным конструктором объектов, при формировании файла кода или внешнего файла сопоставления убедитесь в том, что у них имеется путь к пользовательскому файлу DBML. Хотя этого и не требуется для настройки сопоставления типов, рекомендуется всегда отделять сведения о сопоставлении типов от файла кода и создавать дополнительный внешний файл сопоставления. Это придаст некоторую гибкость, поскольку не придется перекомпилировать файл кода.  
  
## <a name="incorporating-database-changes"></a>Интеграция изменений баз данных  

 При изменении базы данных потребуется обновлять DBML-файл, чтобы он отражал эти изменения. Один из способов реализации этого состоит в автоматическом создании нового DBML-файла и последующем повторном выполнении настройки сопоставления типов. Альтернативный способ заключается в сравнении различий между новым файлом DBML и настроенным файлом DBML и последующем обновлении вручную настроенного DBML-файла, чтобы он отражал изменения базы данных.  
  
## <a name="see-also"></a>См. также раздел

- [Сопоставление типов SQL-CLR](sql-clr-type-mapping.md)
- [Создание кода в LINQ to SQL](code-generation-in-linq-to-sql.md)
