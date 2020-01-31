---
title: Método ICorProfilerCallback::Initialize
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: e4a003b30c495852a3a68d44d92bef35c3ed7812
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866284"
---
# <a name="icorprofilercallbackinitialize-method"></a>Método ICorProfilerCallback::Initialize
Chamado para inicializar o criador de perfil de código sempre que um novo aplicativo Common Language Runtime (CLR) é iniciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parâmetros

- `pICorProfilerInfoUnk`

  \[no] ponteiro para uma interface [IUnknown](/cpp/atl/iunknown) que o criador de perfil deve consultar para um ponteiro de interface [ICorProfilerInfo](icorprofilerinfo-interface.md) .  

## <a name="remarks"></a>Comentários  
 A chamada `Initialize` é a única oportunidade para habilitar (ou desabilitar) retornos de chamada que são imutáveis. Depois que um retorno de chamada é habilitado pelo `Initialize` chamar, ele não pode ser desabilitado posteriormente usando [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md). O valor COR_PRF_MONITOR_IMMUTABLE da enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) indica quais eventos são imutáveis.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método Shutdown](icorprofilercallback-shutdown-method.md)
