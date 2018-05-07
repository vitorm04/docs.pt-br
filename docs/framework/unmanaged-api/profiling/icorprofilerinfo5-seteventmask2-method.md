---
title: ICorProfilerInfo5::Método SetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc1cfadd809b7406845596ace78e308ccbf529a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::Método SetEventMask2
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do tempo de execução de linguagem comum (CLR). Ele fornece a funcionalidade mais do que o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwEventsLow`  
 [in] Um valor de 4 bytes que especifica as categorias de eventos. Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente. Os bits são descritos no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.  
  
 `dwEventsHigh`  
 [in] Um valor de 4 bytes que especifica as categorias de eventos.  Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente. Os bits são descritos no [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeração.  
  
## <a name="remarks"></a>Comentários  
 O método `SetEventMask2` é usado para definir os retornos de chamada para os quais o criador de perfil se inscreve. Normalmente, você chama o [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) método para determinar quais bits são definidos, execute um ou lógico de seu `pdwEventsLow` e `pdwEventsHigh` valores e quaisquer novos bits que você deseja definir e, em seguida, chamar o `SetEventMask2` método.  
  
 Esse método é a alternativa recomendada para o [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [Método GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
