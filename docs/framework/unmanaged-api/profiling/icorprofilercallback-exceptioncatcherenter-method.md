---
title: Метод ICorProfilerCallback::ExceptionCatcherEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 97b9f517a24a7d82b7697cd0723628ede073b537
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700162"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>Метод ICorProfilerCallback::ExceptionCatcherEnter

Уведомляет профилировщик о том, что управление передается соответствующему `catch` блоку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Параметры

- `functionId`

  \[in] идентификатор функции, содержащей `catch` блок.
  
- `objectId`

  \[в] идентификатор обрабатываемого исключения.

## <a name="remarks"></a>Комментарии  

 `ExceptionCatcherEnter`Метод вызывается только в том случае, если точка перехвата находится в коде, скомпилированном с JIT-компилятором. Исключение, перехваченное в неуправляемом коде или во внутреннем коде среды выполнения, не будет вызывать это уведомление. `objectId`Значение передается снова, так как сборка мусора могла переместить объект с момента получения `ExceptionThrown` уведомления.  
  
 Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора. Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.  
  
 Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Метод ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)
