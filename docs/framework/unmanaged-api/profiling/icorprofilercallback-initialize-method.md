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
ms.openlocfilehash: 64df6a81eb23c20537238c702fd0c204d64d14bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434555"
---
# <a name="icorprofilercallbackinitialize-method"></a>Método ICorProfilerCallback::Initialize
Chamado para inicializar o criador de perfil de código sempre que um novo aplicativo Common Language Runtime (CLR) é iniciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pICorProfilerInfoUnk`  
 [na](/cpp/atl/iunknown) interface, o criador de perfil deve consultar um ponteiro de interface [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .  
  
## <a name="remarks"></a>Comentários  
 A chamada `Initialize` é a única oportunidade para habilitar (ou desabilitar) retornos de chamada que são imutáveis. Depois que um retorno de chamada é habilitado pelo `Initialize` chamar, ele não pode ser desabilitado posteriormente usando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). O valor COR_PRF_MONITOR_IMMUTABLE da enumeração [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) indica quais eventos são imutáveis.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
