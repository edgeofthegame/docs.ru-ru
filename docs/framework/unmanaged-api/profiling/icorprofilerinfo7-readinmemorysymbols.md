---
title: 'ICorProfilerInfo7:: Реадинмеморисимболс'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: 6917900b7494550992dfa82f45ed0140f95e68cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733624"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7:: Реадинмеморисимболс

[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]  
  
 Считывает байты из потока символов в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `moduleId`  
 окне Идентификатор модуля, содержащего поток в памяти.  
  
 `symbolsReadOffset`  
 окне Смещение в потоке в памяти, с которого начинается чтение байтов.  
  
 `pSymbolBytes`  
 заполняет Указатель на буфер, в который будут копироваться данные. Буфер должен иметь `countSymbolBytes` доступное место.  
  
 `countSymbolBytes`  
 окне Число байтов для копирования.  
  
 `pCountSymbolBytesRead`  
 заполняет При возврате из метода содержит фактическое число считанных байтов.  
  
## <a name="return-value"></a>Возвращаемое значение  

 `S_OK`значение, если было считано ненулевое число байтов.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, если модуль был создан с помощью <xref:System.Reflection.Emit> .  
  
## <a name="remarks"></a>Комментарии  

 `ReadInMemorySymbols`Метод пытается выполнить чтение `countSymbolBytes` данных, начиная со смещения `symbolsReadOffset` в потоке в памяти. Данные копируются в `pSymbolBytes` , что должно иметь `countSymbolBytes` доступное место.     `pCountSymbolsBytesRead` содержит фактическое число считанных байтов, которое может быть меньше, чем `countSymbolBytes` при достижении конца потока.  
  
> [!NOTE]
> Текущая реализация не поддерживает отражение. Emit. Если модуль был создан с помощью отражения. Emit, метод возвращает значение `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo7](icorprofilerinfo7-interface.md)
