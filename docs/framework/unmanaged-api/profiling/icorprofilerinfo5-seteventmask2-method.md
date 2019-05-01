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
ms.openlocfilehash: 266219894ffefa0d4066c6ca68c7cadf6265e098
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000474"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::Método SetEventMask2
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do tempo de execução de linguagem comum (CLR). Ele fornece mais funcionalidade do que o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwEventsLow`  
 [in] Um valor de 4 bytes que especifica as categorias de eventos. Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente. Os bits são descritos na [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.  
  
 `dwEventsHigh`  
 [in] Um valor de 4 bytes que especifica as categorias de eventos.  Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente. Os bits são descritos na [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeração.  
  
## <a name="remarks"></a>Comentários  
 O método `SetEventMask2` é usado para definir os retornos de chamada para os quais o criador de perfil se inscreve. Normalmente, você chama o [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) método para determinar quais bits são definidos, realizar um OR lógico de seus `pdwEventsLow` e `pdwEventsHigh` valores e qualquer novo bit que você deseja definir e, em seguida, chamar o `SetEventMask2` método.  
  
 Esse método é a alternativa recomendada para o [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [Método GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
