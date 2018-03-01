---
title: Interface ICorProfilerCallback2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7927d3b4d41731c9b69154fa8895a8f698f53e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2-interface"></a>Interface ICorProfilerCallback2
Fornece métodos que são usados pelo common language runtime (CLR) para notificar um criador de perfil de código, quando ocorrem os eventos aos quais o criador de perfil se inscreveu. O `ICorProfilerCallback2` interface é uma extensão do [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface. Ou seja, ele fornece os retornos de chamada novo introduzidos no .NET Framework versão 2.0.  
  
> [!NOTE]
>  Cada implementação do método deve retornar um HRESULT de um valor de S_OK em caso de sucesso ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT retornado por cada retorno de chamada exceto [: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Notifica o criador de perfil de código que um objeto com um finalizador foi enfileirado para o thread do finalizador para execução do seu `Finalize` método.|  
|[Método GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Notifica o criador de perfil que a coleta de lixo foi concluída e todos os retornos de chamada de coleta de lixo foram emitidos por ela.|  
|[Método GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Notifica o criador de perfil de código que iniciou a coleta de lixo.|  
|[Método HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Notifica o criador de perfil de código que foi criado um identificador de coleta de lixo.|  
|[Método HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Notifica o criador de perfil de código que um identificador de coleta de lixo foi destruído.|  
|[Método RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Notifica o criador de perfil sobre referências da raiz após a conclusão de uma coleta de lixo. Esse método é uma extensão do [: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) método.|  
|[Método SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Notifica o criador de perfil sobre referências de objeto que tem sobreviveram a uma coleta de lixo.|  
|[Método ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Notifica o criador de perfil de código que o nome de um thread foi alterado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama um método `ICorProfilerCallback` (ou `ICorProfilerCallback2`) interface para notificar o criador de perfil quando um evento, em que o criador de perfil tinha inscrita, ocorre. Essa é a interface de retorno de chamada primário por meio dos quais o CLR se comunica com o criador de perfil de código.  
  
 Um criador de perfil de código deve implementar os métodos do `ICorProfilerCallback` interface. Para o .NET Framework 2.0 e versões posteriores, o criador de perfil também deve implementar o `ICorProfilerCallback2` métodos. Cada implementação do método deve retornar um HRESULT de um valor de S_OK em caso de sucesso ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT retornado por cada retorno de chamada exceto [: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Um criador de perfil de código deve registrar no registro do Microsoft Windows, o objeto COM que implementa o `ICorProfilerCallback` e `ICorProfilerCallback2` interfaces. Um criador de perfil de código assina os eventos para os quais deseja receber notificação chamando [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Geralmente, isso é feito na implementação do criador de perfil do [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). O criador de perfil, em seguida, é capaz de receber a notificação de tempo de execução quando um evento está prestes a ocorrer, ou apenas ocorreu em um processo em execução do tempo de execução.  
  
> [!NOTE]
>  O criador de perfil registra um único objeto COM. Se o criador de perfil está voltado para o .NET Framework versão 1.0 ou 1.1, esse objeto COM só precisa implementar os métodos de `ICorProfilerCallback`. Se ele está direcionando o .NET Framework versão 2.0 e versões posteriores, o objeto COM também deve implementar os métodos de `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
