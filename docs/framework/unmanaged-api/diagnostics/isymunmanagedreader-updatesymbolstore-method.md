---
title: Метод ISymUnmanagedReader::UpdateSymbolStore
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: 6670d985eed4c55550b23d3f4110ee20f3b75661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675832"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>Метод ISymUnmanagedReader::UpdateSymbolStore

Обновляет существующее хранилище символов разностным хранилищем символов. Этот метод используется в сценариях "изменить и продолжить" для обновления хранилища символов в соответствии с разностью с исходным переносимым исполняемым файлом (PE).  
  
> [!NOTE]
> Необходимо указать только один из `filename` `pIStream` параметров или, но не оба. Если `filename` указан параметр, хранилище символов будет обновлено символами из этого файла. Если `pIStream` указан параметр, хранилище будет обновляться данными из <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Параметры  

 `filename`  
 окне Имя файла, содержащего хранилище символов.  
  
 `pIStream`  
 окне Файловый поток, используемый в качестве альтернативы `filename` параметру.  
  
## <a name="return-value"></a>Возвращаемое значение  

 S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.  
  
## <a name="requirements"></a>Требования  

 **Заголовок:** Корсим. idl, Корсим. h  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ISymUnmanagedReader](isymunmanagedreader-interface.md)
