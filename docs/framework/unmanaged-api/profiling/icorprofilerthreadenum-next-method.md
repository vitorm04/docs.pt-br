---
title: Método ICorProfilerThreadEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
ms.openlocfilehash: e78285c915938c553a9b4012ba57257ac43492ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447602"
---
# <a name="icorprofilerthreadenumnext-method"></a>Método ICorProfilerThreadEnum::Next
Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] The number of threads to retrieve.  
  
 `ids`  
 [out] An array of `ThreadID` values, each of which represents a retrieved thread.  
  
 `pceltFetched`  
 [out] A pointer to the number of threads actually returned in the `ids` array.  
  
## <a name="return-value"></a>Valor retornado  
 This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`celt` elements were returned.|  
|S_FALSE|Fewer than `celt` elements were returned, which indicates that the enumeration is complete.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
