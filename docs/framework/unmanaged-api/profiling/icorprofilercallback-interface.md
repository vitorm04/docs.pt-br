---
title: Interface ICorProfilerCallback
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3119818934df765a8bbd9c05caaee04f9476069f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963516"
---
# <a name="icorprofilercallback-interface"></a>Interface ICorProfilerCallback
Fornece métodos que são usados pelo Common Language Runtime (CLR) para notificar um criador de perfil de código quando os eventos para os quais o criador de perfil assinou ocorreram.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Notifica o criador de perfil de que um domínio de aplicativo foi criado.|  
|[Método AppDomainCreationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Notifica o criador de perfil de que um domínio de aplicativo está sendo criado.|  
|[Método AppDomainShutdownFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Notifica o criador de perfil de que um domínio de aplicativo foi descarregado de um processo.|  
|[Método AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Notifica o criador de perfil de que um domínio de aplicativo está sendo descarregado de um processo.|  
|[Método AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Notifica o criador de perfil que concluiu o carregamento de um assembly.|  
|[Método AssemblyLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Notifica o criador de perfil de que um assembly está sendo carregado.|  
|[Método AssemblyUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Notifica o criador de perfil de que um assembly foi descarregado.|  
|[Método AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Notifica o criador de perfil de que um assembly está sendo descarregado.|  
|[Método ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Notifica o criador de perfil que a conclusão do carregamento de uma classe.|  
|[Método ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Notifica o criador de perfil de que uma classe está sendo carregada.|  
|[Método ClassUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Notifica o criador de perfil de que uma classe concluiu o descarregamento.|  
|[Método ClassUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Notifica o criador de perfil de que uma classe está sendo descarregada.|  
|[Método COMClassicVTableCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Notifica o criador de perfil de que um RCW (Runtime Callable Wrapper) para o IID e a classe especificados foram criados.|  
|[Método COMClassicVTableDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Notifica o criador de perfil de que um RCW está sendo destruído.|  
|[Método ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Notifica o criador de perfil que o controle está sendo passado para `catch` o bloco apropriado.|  
|[Método ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Notifica o criador de perfil que o controle está sendo passado para fora `catch` do bloco apropriado.|  
|[Método ExceptionCLRCatcherExecute](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Obsoleto no .NET Framework versão 2,0.|  
|[Método ExceptionCLRCatcherFound](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Obsoleto no .NET Framework 2,0.|  
|[Método ExceptionOSHandlerEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Não implementado. Um criador de perfil que precisa de informações de exceção não gerenciadas deve obter essas informações por meio de outros meios.|  
|[Método ExceptionOSHandlerLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Não implementado. Um criador de perfil que precisa de informações de exceção não gerenciadas deve obter essas informações por meio de outros meios.|  
|[Método ExceptionSearchCatcherFound](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Notifica o criador de perfil de que a fase de pesquisa do tratamento de exceções localizou um manipulador para a exceção que foi lançada.|  
|[Método ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Notifica o criador de perfil de que um filtro de usuário está sendo executado.|  
|[Método ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Notifica o criador de perfil de que um filtro de usuário acabou de executar a execução.|  
|[Método ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Notifica o criador de perfil de que a fase de pesquisa do tratamento de exceções inseriu uma função.|  
|[Método ExceptionSearchFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Notifica o criador de perfil de que a fase de pesquisa do tratamento de exceções concluiu a pesquisa de uma função.|  
|[Método ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Notifica o criador de perfil de que uma exceção foi lançada.|  
|[Método ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Notifica o criador de perfil de que a fase de desenrolamento da `finally` manipulação de exceção está inserindo uma cláusula contida na função especificada.|  
|[Método ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Notifica o criador de perfil de que a fase de desenrolamento da `finally` manipulação de exceção saiu de uma cláusula.|  
|[Método ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Notifica o criador de perfil de que a fase de desenrolar da manipulação de exceções inseriu uma função.|  
|[Método ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Notifica o criador de perfil de que a fase de desenrolamento da manipulação de exceções concluiu o desenrolamento de uma função.|  
|[Método FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Notifica o criador de perfil de que o tempo de execução começou a descarregar uma função.|  
|[Método Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Chamado para inicializar o criador de perfil sempre que um novo aplicativo CLR é iniciado.|  
|[Método JITCachedFunctionSearchFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Notifica o criador de perfil de que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando NGen. exe.|  
|[Método JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Notifica o criador de perfil de que uma pesquisa foi iniciada para uma função que foi compilada anteriormente usando NGen. exe.|  
|[Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Notifica o criador de perfil de que o compilador JIT concluiu a compilação de uma função.|  
|[Método JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a compilar uma função.|  
|[Método JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Notifica o criador de perfil de que uma função que foi compilada por JIT foi removida da memória.|  
|[Método JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Notifica o criador de perfil de que o compilador JIT está prestes a inserir uma função em linha com outra função.|  
|[Método ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Notifica o criador de perfil de que uma transição do código gerenciado para o código não gerenciado ocorreu.|  
|[Método ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Notifica o criador de perfil de que um módulo está sendo anexado a seu assembly pai.|  
|[Método ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Notifica o criador de perfil que concluiu o carregamento de um módulo.|  
|[Método ModuleLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Notifica o criador de perfil de que um módulo está sendo carregado.|  
|[Método ModuleUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Notifica o criador de perfil de que um módulo concluiu o descarregamento.|  
|[Método ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Notifica o criador de perfil de que um módulo está sendo descarregado.|  
|[Método MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Notifica o criador de perfil sobre referências de objeto que foram movidas durante a coleta de lixo.|  
|[Método ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Notifica o criador de perfil de que a memória dentro do heap foi alocada para um objeto.|  
|[Método ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Notifica o criador de perfil sobre objetos na memória referenciados pelo objeto especificado.|  
|[Método ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criadas desde a coleta de lixo anterior.|  
|[Método RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Notifica o criador de perfil de que uma chamada de comunicação remota foi executada até a conclusão no cliente.|  
|[Método RemotingClientInvocationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Notifica o criador de perfil de que uma chamada de comunicação remota foi iniciada.|  
|[Método RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Notifica o criador de perfil de que a parte do lado do servidor de uma chamada de comunicação remota foi concluída e que o cliente agora está recebendo e prestes a processar a resposta.|  
|[Método RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Notifica o criador de perfil de que o cliente está enviando uma solicitação para o servidor.|  
|[Método RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Notifica o criador de perfil de que o processo concluiu a invocação de um método em resposta a uma solicitação de invocação de método remoto.|  
|[Método RemotingServerInvocationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Notifica o criador de perfil de que o processo está invocando um método em resposta a uma solicitação de invocação de método remoto.|  
|[Método RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Notifica o criador de perfil de que o processo está recebendo uma invocação de método remoto ou uma solicitação de ativação.|  
|[Método RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Notifica o criador de perfil de que o processo concluiu o processamento de uma solicitação de invocação de método remoto e está prestes a transmitir a resposta por meio de um canal.|  
|[Método RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Notifica o criador de perfil com informações sobre referências raiz após a coleta de lixo.|  
|[Método RuntimeResumeFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Notifica o criador de perfil de que o tempo de execução retomou todos os threads de tempo de execução e retornou à operação normal.|  
|[Método RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Notifica o criador de perfil de que o tempo de execução está retomando todos os threads em tempo de execução.|  
|[Método RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Notifica o criador de perfil de que o tempo de execução anulou a suspensão de runtime que estava ocorrendo.|  
|[Método RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Notifica o criador de perfil de que o tempo de execução concluiu a suspensão de todos os threads em tempo de execução.|  
|[Método RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Notifica o criador de perfil de que o tempo de execução está prestes a suspender todos os threads em tempo de execução.|  
|[Método RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Notifica o criador de perfil de que o thread especificado foi retomado após ser suspenso.|  
|[Método RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Notifica o criador de perfil de que o thread especificado foi ou está prestes a ser suspenso.|  
|[Método Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Notifica o criador de perfil de que o aplicativo está sendo desligado.|  
|[Método ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Notifica o criador de perfil de que um thread gerenciado está sendo implementado usando um determinado thread de sistema operacional (SO).|  
|[Método ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Notifica o criador de perfil de que um thread foi criado.|  
|[Método ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Notifica o criador de perfil de que um thread foi destruído.|  
|[Método UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Notifica o criador de perfil de que uma transição de código não gerenciado para código gerenciado ocorreu.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama um método na `ICorProfilerCallback` interface (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) para notificar o criador de perfil quando um evento, ao qual o criador de perfil assinou, ocorre. Essa é a interface de retorno de chamada principal por meio da qual o CLR se comunica com o criador de perfil de código.  
  
 Um criador de perfil de código deve implementar os `ICorProfilerCallback` métodos da interface. Para o .NET Framework versão 2,0 ou posterior, o criador de perfil também deve `ICorProfilerCallback2` implementar os métodos. Cada implementação de método deve retornar um HRESULT que tenha um valor de S_OK em sucesso ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT que é retornado por cada retorno de chamada, exceto [ICorProfilerCallback::](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)objectreferenciations.  
  
 No registro do Microsoft Windows, um criador de perfil de código deve registrar seu objeto de Component Object Model (com `ICorProfilerCallback` ) `ICorProfilerCallback2` que implementa as interfaces e. Um criador de perfil de código assina os eventos para os quais deseja receber notificação chamando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Isso geralmente é feito na implementação do criador de perfil de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Em seguida, o criador de perfil é capaz de receber a notificação do tempo de execução quando um evento está prestes a ocorrer ou ocorreu apenas em um processo de tempo de execução.  
  
> [!NOTE]
> O criador de perfil registra um único objeto COM. Se o criador de perfil estiver direcionando para o .NET Framework versão 1,0 ou 1,1, esse objeto COM precisará implementar `ICorProfilerCallback`apenas os métodos de. Se ele estiver direcionando .NET Framework versão 2,0 ou posterior, o objeto COM também deverá implementar os métodos `ICorProfilerCallback2`de.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
