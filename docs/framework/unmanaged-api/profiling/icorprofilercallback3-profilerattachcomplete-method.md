---
title: "Método ICorProfilerCallback3::ProfilerAttachComplete"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.ProfilerAttachComplete Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0bf1e535c6270660797554c38a0b031df82f0925
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>Método ICorProfilerCallback3::ProfilerAttachComplete
Chamado pelo common language runtime (CLR) para indicar que o criador de perfil agora pode chamar o [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) e [Icorprofilerinfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) métodos de recuperação do atraso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Comentários  
 O `ProfilerAttachComplete` retorno de chamada é emitido após o [Icorprofilercallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) método é chamado. Ele indica o seguinte:  
  
-   Os retornos de chamada que foram solicitados pelo criador de perfil em `InitializeForAttach` ter sido ativado.  
  
-   O criador de perfil agora pode realizar a varredura em associado identificações, sem estar preocupadas com notificações ausentes.  
  
 O CLR ignora o valor de retorno desse retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
