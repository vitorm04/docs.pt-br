---
title: Método ICorProfilerCallback3::ProfilerAttachComplete
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865422"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>Método ICorProfilerCallback3::ProfilerAttachComplete
Chamado pelo Common Language Runtime (CLR) para indicar que o criador de perfil agora pode chamar os métodos de atualização [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) e [ICorProfilerInfo3:: EnumModules](icorprofilerinfo3-enummodules-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada `ProfilerAttachComplete` é emitido depois que o método [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) é chamado. Isso indica o seguinte:  
  
- Os retornos de chamada que foram solicitados pelo criador de perfil no `InitializeForAttach` foram ativados.  
  
- O criador de perfil agora pode realizar a atualização nas IDs associadas sem se preocupar com notificações ausentes.  
  
 O CLR ignora o valor de retorno deste retorno de chamada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Interface ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
