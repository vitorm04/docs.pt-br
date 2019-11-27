---
title: Interface ICorProfilerCallback3
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 25d674a143019ac5d724e36f03f36c79602b1e11
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439500"
---
# <a name="icorprofilercallback3-interface"></a>Interface ICorProfilerCallback3
Fornece métodos de retorno de chamada que o Common Language Runtime (CLR) usa para comunicar a anexação e desanexar informações de estado ao criador de perfil.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|Chamado pelo CLR para dar ao criador de perfil uma oportunidade de inicializar seu estado após uma operação de anexação.|  
|[Método ProfilerAttachComplete](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|Chamado pelo CLR para indicar que o criador de perfil agora pode chamar os métodos de atualização.|  
|[Método ProfilerDetachSucceeded](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|Notifica o criador de perfil de que o Common Language Runtime (CLR) está prestes a descarregar a DLL do criador de perfil.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
