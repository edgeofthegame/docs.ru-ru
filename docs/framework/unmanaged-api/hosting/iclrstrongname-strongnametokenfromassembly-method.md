---
title: Метод ICLRStrongName::StrongNameTokenFromAssembly
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: 90a7e60e35e1fc555681102ffa62967eb5ac01fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671542"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a>Метод ICLRStrongName::StrongNameTokenFromAssembly

Создает маркер строгого имени из указанного файла сборки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `wszFilePath`  
 окне Путь к переносимому исполняемому файлу (PE) для сборки.  
  
 `ppbStrongNameToken`  
 заполняет Возвращенный маркер строгого имени.  
  
 `pcbStrongNameToken`  
 заполняет Размер (в байтах) маркера строгого имени.  
  
## <a name="return-value"></a>Возвращаемое значение  

 `S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).  
  
## <a name="remarks"></a>Комментарии  

 Маркер строгого имени — это сокращенная форма открытого ключа. Маркер представляет собой 64-разрядный хэш, созданный из открытого ключа, используемого для подписания сборки. Токен является частью строгого имени сборки и может быть считан из метаданных сборки.  
  
 После создания маркера следует вызвать метод [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) , чтобы освободить выделенную память.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** Метахост. h  
  
 **Библиотека:** Включается в качестве ресурса в MSCorEE.dll  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Метод StrongNameTokenFromAssemblyEx](iclrstrongname-strongnametokenfromassemblyex-method.md)
- [Интерфейс ICLRStrongName](iclrstrongname-interface.md)
