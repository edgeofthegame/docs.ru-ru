---
title: Интерфейс ICorDebugModule
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 86e17b48bc491c45f8b46be23ab626dc1f2a6962
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709847"
---
# <a name="icordebugmodule-interface"></a>Интерфейс ICorDebugModule

Представляет модуль среды CLR, который является либо исполняемым файлом, либо библиотекой динамической компоновки (DLL).  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод CreateBreakpoint](icordebugmodule-createbreakpoint-method.md)|Не реализован.|  
|[Метод EnableClassLoadCallbacks](icordebugmodule-enableclassloadcallbacks-method.md)|Определяет, вызываются ли для этого модуля обратные вызовы [ICorDebugManagedCallback:: loadClass](icordebugmanagedcallback-loadclass-method.md) и [ICorDebugManagedCallback:: унлоадкласс](icordebugmanagedcallback-unloadclass-method.md) .|  
|[Метод EnableJITDebugging](icordebugmodule-enablejitdebugging-method.md)|Определяет, будет ли JIT-компилятор сохранить отладочную информацию для методов в этом модуле.|  
|[Метод GetAssembly](icordebugmodule-getassembly-method.md)|Возвращает содержащуюся сборку для этого модуля.|  
|[Метод GetBaseAddress](icordebugmodule-getbaseaddress-method.md)|Возвращает базовый адрес модуля.|  
|[Метод GetClassFromToken](icordebugmodule-getclassfromtoken-method.md)|Возвращает ICorDebugClass из метаданных.|  
|[Метод GetEditAndContinueSnapshot](icordebugmodule-geteditandcontinuesnapshot-method.md)|Не рекомендуется.|  
|[Метод GetFunctionFromRVA](icordebugmodule-getfunctionfromrva-method.md)|Не реализован.|  
|[Метод GetFunctionFromToken](icordebugmodule-getfunctionfromtoken-method.md)|Возвращает функцию, заданную маркером метаданных.|  
|[Метод GetGlobalVariableValue](icordebugmodule-getglobalvariablevalue-method.md)|Возвращает объект значения для указанной глобальной переменной.|  
|[Метод GetMetaDataInterface](icordebugmodule-getmetadatainterface-method.md)|Возвращает указатель интерфейса метаданных, который может использоваться для проверки метаданных модуля.|  
|[Метод GetName](icordebugmodule-getname-method.md)|Возвращает имя файла модуля.|  
|[Метод GetProcess](icordebugmodule-getprocess-method.md)|Возвращает содержащий процесс для этого модуля.|  
|[Метод GetSize](icordebugmodule-getsize-method.md)|Возвращает размер модуля в байтах.|  
|[Метод GetToken](icordebugmodule-gettoken-method.md)|Возвращает маркер для записи таблицы для этого модуля.|  
|[Метод IsDynamic](icordebugmodule-isdynamic-method.md)|Указывает, является ли модуль динамическим.|  
|[Метод IsInMemory](icordebugmodule-isinmemory-method.md)|Указывает, существует ли этот модуль только в памяти.|  
  
## <a name="remarks"></a>Комментарии  
  
> [!NOTE]
> Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorDebug](icordebug-interface.md)
- [Интерфейсы отладки](debugging-interfaces.md)
