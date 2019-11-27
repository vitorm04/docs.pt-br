---
title: Interface ICorProfilerCallback4
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: a3394820f673e35777e1749229d4f8319841ca58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439383"
---
# <a name="icorprofilercallback4-interface"></a>Interface ICorProfilerCallback4
Fornece métodos de retorno de chamada que o Common Language Runtime (CLR) usa para comunicar informações ao criador de perfil.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|Permite que o criador de perfil de código defina sinalizadores de geração de código alternativos para um novo corpo de método recompilado.|  
|[Método MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|Relata o novo layout de objetos no heap como resultado de uma coleta de lixo de compactação.|  
|[Método ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|Notifica o criador de perfil de que o compilador JIT (just-in-time) concluiu a recompilação de uma função.|  
|[Método ReJITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a recompilar uma função.|  
|[Método ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|Relata um erro encontrado durante o processamento de uma solicitação de recompilação.|  
|[Método SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
