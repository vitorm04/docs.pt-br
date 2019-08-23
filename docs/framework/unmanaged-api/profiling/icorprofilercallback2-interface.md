---
title: Interface ICorProfilerCallback2
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d36d8ef3bfdbd6a1acf787a91003e2ff3139a4d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963961"
---
# <a name="icorprofilercallback2-interface"></a>Interface ICorProfilerCallback2
Fornece métodos que são usados pelo Common Language Runtime (CLR) para notificar um criador de perfil de código quando os eventos para os quais o criador de perfil assinou ocorreram. A `ICorProfilerCallback2` interface é uma extensão da interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) . Ou seja, ele fornece novos retornos de chamada introduzidos na versão .NET Framework 2,0.  
  
> [!NOTE]
> Cada implementação de método deve retornar um HRESULT com valor de S_OK em sucesso ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT que é retornado por cada retorno de chamada, exceto [ICorProfilerCallback::](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)objectreferenciations.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Notifica o criador de perfil de código de que um objeto com um finalizador foi enfileirado para o thread do finalizador `Finalize` para execução de seu método.|  
|[Método GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Notifica o criador de perfil de que uma coleta de lixo foi concluída e todos os retornos de chamada de coleta de lixo foram emitidos para ela.|  
|[Método GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Notifica o criador de perfil de código de que uma coleta de lixo foi iniciada.|  
|[Método HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Notifica o criador de perfil de código de que um identificador de coleta de lixo foi criado.|  
|[Método HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Notifica o criador de perfil de código de que um identificador de coleta de lixo foi destruído.|  
|[Método RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Notifica o criador de perfil sobre referências de raiz após a ocorrência de uma coleta de lixo. Esse método é uma extensão do método [ICorProfilerCallback:: RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) .|  
|[Método SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Notifica o criador de perfil sobre referências de objeto que têm sobreviveram uma coleta de lixo.|  
|[Método ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Notifica o criador de perfil de código de que o nome de um thread foi alterado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama um método na `ICorProfilerCallback` interface (ou `ICorProfilerCallback2`) para notificar o criador de perfil quando um evento, ao qual o criador de perfil tinha se inscrito, ocorre. Essa é a interface de retorno de chamada principal por meio da qual o CLR se comunica com o criador de perfil de código.  
  
 Um criador de perfil de código deve implementar os `ICorProfilerCallback` métodos da interface. Para o .NET Framework 2,0 e versões posteriores, o criador de perfil também `ICorProfilerCallback2` deve implementar os métodos. Cada implementação de método deve retornar um HRESULT com valor de S_OK em sucesso ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT que é retornado por cada retorno de chamada, exceto [ICorProfilerCallback::](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)objectreferenciations.  
  
 Um criador de perfil de código deve se registrar no registro do Microsoft Windows, seu objeto `ICorProfilerCallback` com `ICorProfilerCallback2` que implementa as interfaces e. Um criador de perfil de código assina os eventos para os quais deseja receber notificação chamando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Isso geralmente é feito na implementação do criador de perfil de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Em seguida, o criador de perfil é capaz de receber a notificação do tempo de execução quando um evento está prestes a ocorrer ou ocorreu apenas em um processo de tempo de execução.  
  
> [!NOTE]
> O criador de perfil registra um único objeto COM. Se o criador de perfil estiver direcionando .NET Framework versão 1,0 ou 1,1, esse objeto COM precisará implementar `ICorProfilerCallback`apenas os métodos de. Se ele estiver direcionando .NET Framework versão 2,0 e posterior, o objeto COM também deverá implementar os métodos `ICorProfilerCallback2`de.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
