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
ms.openlocfilehash: 513fb623e328a8fa3abb1531715026ff9b6bf97e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558079"
---
# <a name="icorprofilercallback2-interface"></a>Interface ICorProfilerCallback2
Fornece métodos que são usados pelo common language runtime (CLR) para notificar um criador de perfil de código quando ocorrem os eventos que assinou o criador de perfil. O `ICorProfilerCallback2` interface é uma extensão do [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface. Ou seja, ele fornece os retornos de chamada novo introduzidos no .NET Framework versão 2.0.  
  
> [!NOTE]
>  Cada implementação do método deve retornar um HRESULT que tem um valor de S_OK no êxito ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT retornado por cada retorno de chamada, exceto [ICorProfilerCallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Notifica o criador de perfil de código que um objeto com um finalizador foi enfileirado para o thread do finalizador para a execução de seu `Finalize` método.|  
|[Método GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Notifica o criador de perfil que uma coleta de lixo foi concluída e todos os retornos de chamada de coleta de lixo tiveram sido emitidos para ele.|  
|[Método GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Notifica o criador de perfil de código que uma coleta de lixo foi iniciada.|  
|[Método HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Notifica o criador de perfil de código que foi criado um identificador da coleta de lixo.|  
|[Método HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Notifica o criador de perfil de código que um identificador da coleta de lixo foi destruído.|  
|[Método RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Notifica o criador de perfil sobre referências raiz após a ocorrência de uma coleta de lixo. Esse método é uma extensão de [ICorProfilerCallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) método.|  
|[Método SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Notifica o criador de perfil sobre referências de objetos que sobreviveram a uma coleta de lixo.|  
|[Método ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Notifica o criador de perfil de código que o nome de um thread foi alterado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama um método na `ICorProfilerCallback` (ou `ICorProfilerCallback2`) ocorre de interface para notificar quando um evento ao qual o criador de perfil tivesse assinado, o criador de perfil. Essa é a interface de retorno de chamada de primária por meio do qual o CLR se comunica com o criador de perfil de código.  
  
 Um criador de perfil de código deve implementar os métodos do `ICorProfilerCallback` interface. Para o .NET Framework 2.0 e versões posteriores, o criador de perfil também deve implementar o `ICorProfilerCallback2` métodos. Cada implementação do método deve retornar um HRESULT que tem um valor de S_OK no êxito ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT retornado por cada retorno de chamada, exceto [ICorProfilerCallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Um criador de perfil de código deve se registrar no registro do Microsoft Windows, seu objeto COM que implementa o `ICorProfilerCallback` e `ICorProfilerCallback2` interfaces. Um criador de perfil de código assina os eventos para os quais deseja receber notificação chamando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Geralmente, isso é feito na implementação do criador de perfil do [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). O criador de perfil, em seguida, é capaz de receber a notificação de tempo de execução quando um evento está prestes a ocorrer ou se ocorreu em um processo em execução de tempo de execução.  
  
> [!NOTE]
>  O criador de perfil registra um único objeto COM. Se o criador de perfil for destinado ao .NET Framework versão 1.0 ou 1.1, esse objeto COM só precisa implementar os métodos de `ICorProfilerCallback`. Se ele é direcionado ao .NET Framework versão 2.0 e versões posteriores, o objeto COM também deve implementar os métodos de `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
