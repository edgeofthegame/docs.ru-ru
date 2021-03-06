---
title: Практическое руководство. Создание коллекции с помощью инициализатора набора
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: b332ffb44ebc20ce8431e586fc380b8c6a29967d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086378"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Практическое руководство. Создание коллекции, используемой инициализатором набора (Visual Basic)

При использовании инициализатора коллекции для создания коллекции компилятор Visual Basic выполняет поиск `Add` метода типа коллекции, для которого параметры `Add` метода соответствуют типам значений в инициализаторе коллекции. Этот `Add` метод используется для заполнения коллекции значениями из инициализатора коллекции.  
  
## <a name="example"></a>Пример  

 В следующем примере показана `OrderCollection` коллекция, содержащая открытый `Add` метод, который инициализатор коллекции может использовать для добавления объектов типа `Order` . `Add`Метод позволяет использовать сокращенный синтаксис инициализатора коллекции.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>См. также

- [Инициализаторы коллекций](index.md)
- [Практическое руководство. Создание метода добавления расширения, используемого инициализатором коллекции](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
