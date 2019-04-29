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
ms.openlocfilehash: e2f474317493b3aac421ca1270ff461b97cfe027
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598059"
---
# <a name="icorprofilercallback-interface"></a>Interface ICorProfilerCallback
Fornece métodos que são usados pelo common language runtime (CLR) para notificar um criador de perfil de código quando ocorrem os eventos que assinou o criador de perfil.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Notifica o criador de perfil que foi criado um domínio de aplicativo.|  
|[Método AppDomainCreationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Notifica o criador de perfil que está sendo criado um domínio de aplicativo.|  
|[Método AppDomainShutdownFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Notifica o criador de perfil que um domínio de aplicativo foi descarregado de um processo.|  
|[Método AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Notifica o criador de perfil que um domínio de aplicativo está sendo descarregado de um processo.|  
|[Método AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Notifica o criador de perfil um assembly terminou o carregamento.|  
|[Método AssemblyLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Notifica o criador de perfil que um assembly que está sendo carregado.|  
|[Método AssemblyUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Notifica o criador de perfil que um assembly foi descarregado.|  
|[Método AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Notifica o criador de perfil que um assembly que está sendo descarregado.|  
|[Método ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Notifica o criador de perfil de uma classe terminou o carregamento.|  
|[Método ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Notifica o criador de perfil que uma classe está sendo carregada.|  
|[Método ClassUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Notifica o criador de perfil que uma classe concluiu a descarregar.|  
|[Método ClassUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Notifica o criador de perfil que uma classe está sendo descarregada.|  
|[Método COMClassicVTableCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Notifica o criador de perfil que foi criado um runtime callable wrapper (RCW) para o IID e a classe especificada.|  
|[Método COMClassicVTableDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Notifica o criador de perfil que está sendo destruído um RCW.|  
|[Método ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Notifica o criador de perfil que o controle está sendo passado para o apropriada `catch` bloco.|  
|[Método ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Notifica o criador de perfil que está sendo passado o controle fora apropriado `catch` bloco.|  
|[Método ExceptionCLRCatcherExecute](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Obsoleto no .NET Framework versão 2.0.|  
|[Método ExceptionCLRCatcherFound](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Obsoleto no .NET Framework 2.0.|  
|[Método ExceptionOSHandlerEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Não implementado. Um criador de perfil que precisa de informações de exceção não gerenciado deve obter essas informações por outros meios.|  
|[Método ExceptionOSHandlerLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Não implementado. Um criador de perfil que precisa de informações de exceção não gerenciado deve obter essas informações por outros meios.|  
|[Método ExceptionSearchCatcherFound](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Notifica o criador de perfil que a fase de pesquisa de manipulação de exceção foi localizado um manipulador para a exceção que foi gerada.|  
|[Método ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Notifica o criador de perfil que um filtro de usuário está sendo executado.|  
|[Método ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Notifica o criador de perfil que um filtro de usuário concluiu a execução.|  
|[Método ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Notifica o criador de perfil que a fase de pesquisa de tratamento de exceções entrou em uma função.|  
|[Método ExceptionSearchFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Notifica o criador de perfil que a fase de pesquisa de tratamento de exceções concluiu a pesquisa a uma função.|  
|[Método ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Notifica o criador de perfil que foi lançada uma exceção.|  
|[Método ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Notifica o criador de perfil que a fase de desenrolamento de exceção de manipulação está inserindo um `finally` cláusula contida na função especificada.|  
|[Método ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Notifica o criador de perfil que a fase de desenrolamento de exceção tratamento deixou um `finally` cláusula.|  
|[Método ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Notifica o criador de perfil que a fase de desenrolamento de tratamento de exceções entrou em uma função.|  
|[Método ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Notifica o criador de perfil que a fase de desenrolamento de tratamento de exceções terminou o desenrolamento de uma função.|  
|[Método FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Notifica o criador de perfil que o tempo de execução foi iniciada descarregar uma função.|  
|[Método Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Chamado para inicializar o criador de perfil sempre que um novo aplicativo de CLR é iniciado.|  
|[Método JITCachedFunctionSearchFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Notifica o criador de perfil que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando NGen.exe.|  
|[Método JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Notifica o criador de perfil que uma pesquisa foi iniciada para uma função que foi compilada anteriormente usando NGen.exe.|  
|[Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Notifica o criador de perfil que o compilador JIT concluiu a compilação de uma função.|  
|[Método JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Notifica o criador de perfil que o compilador just-in-time (JIT) começou a compilar uma função.|  
|[Método JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Notifica o criador de perfil que uma função que tenha sido compilado por JIT foi removida da memória.|  
|[Método JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Notifica o criador de perfil que o compilador JIT está prestes a inserir uma função alinhada com outra função.|  
|[Método ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Notifica o criador de perfil que ocorreu uma transição de código gerenciado para código não gerenciado.|  
|[Método ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Notifica o criador de perfil que um módulo está sendo anexado ao seu assembly pai.|  
|[Método ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Notifica o criador de perfil de um módulo terminou o carregamento.|  
|[Método ModuleLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Notifica o criador de perfil que um módulo está sendo carregado.|  
|[Método ModuleUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Notifica o criador de perfil que um módulo tenha terminado de descarregamento.|  
|[Método ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Notifica o criador de perfil que um módulo está sendo descarregado.|  
|[Método MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Notifica o criador de perfil sobre referências de objeto que foram movidos durante a coleta de lixo.|  
|[Método ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Notifica o criador de perfil que foi alocada para um objeto de memória no heap.|  
|[Método ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Notifica o criador de perfil sobre objetos em memória referenciada pelo objeto especificado.|  
|[Método ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criados desde a coleta de lixo anterior.|  
|[Método RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Notifica o criador de perfil que uma chamada de comunicação remota foi executado até a conclusão no cliente.|  
|[Método RemotingClientInvocationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Notifica o criador de perfil que uma chamada de comunicação remota foi iniciada.|  
|[Método RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Notifica o criador de perfil que a parte do lado do servidor de uma chamada de comunicação remota foi concluída e o cliente agora está recebendo e prestes a processar a resposta.|  
|[Método RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Notifica o criador de perfil que o cliente está enviando uma solicitação ao servidor.|  
|[Método RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Notifica o criador de perfil que o processo foi concluído invocando um método em resposta a uma solicitação de invocação de método remoto.|  
|[Método RemotingServerInvocationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Notifica o criador de perfil que o processo está invocando um método em resposta a uma solicitação de invocação de método remoto.|  
|[Método RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Notifica o criador de perfil que o processo está recebendo uma solicitação de ativação ou invocação de método remoto.|  
|[Método RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Notifica o criador de perfil que o processo terminou de processar uma solicitação de invocação de método remoto e está prestes a transmitir a resposta por meio de um canal.|  
|[Método RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Notifica o criador de perfil com informações sobre referências raiz após a coleta de lixo.|  
|[Método RuntimeResumeFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Notifica o criador de perfil que o tempo de execução foi retomada todos os threads de tempo de execução e retornou para operação normal.|  
|[Método RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Notifica o criador de perfil que o tempo de execução está continuando todos os threads de tempo de execução.|  
|[Método RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Notifica o criador de perfil que o tempo de execução foi anulada a suspensão de tempo de execução que estava ocorrendo.|  
|[Método RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Notifica o criador de perfil que o tempo de execução foi concluída a suspensão de todos os segmentos de tempo de execução.|  
|[Método RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Notifica o criador de perfil que o tempo de execução está prestes a suspender todos os segmentos de tempo de execução.|  
|[Método RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Notifica o criador de perfil que o thread especificado foi retomada após ter sido suspenso.|  
|[Método RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Notifica o criador de perfil que o thread especificado foi ou está prestes a ser, suspenso.|  
|[Método Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Notifica o criador de perfil que o aplicativo está sendo desligado.|  
|[Método ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Notifica o criador de perfil que um thread gerenciado está sendo implementado usando um thread de determinado sistema operacional (SO).|  
|[Método ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Notifica o criador de perfil que um thread foi criado.|  
|[Método ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Notifica o criador de perfil que um thread foi destruído.|  
|[Método UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Notifica o criador de perfil que ocorreu uma transição de código não gerenciado para código gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama um método na `ICorProfilerCallback` (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) ocorre de interface para notificar quando um evento ao qual o criador de perfil tenha assinado, o criador de perfil. Essa é a interface de retorno de chamada de primária por meio do qual o CLR se comunica com o criador de perfil de código.  
  
 Um criador de perfil de código deve implementar os métodos do `ICorProfilerCallback` interface. Para o .NET Framework versão 2.0 ou posterior, o criador de perfil também deve implementar o `ICorProfilerCallback2` métodos. Cada implementação do método deve retornar um HRESULT que tem um valor de S_OK no êxito ou E_FAIL em caso de falha. Atualmente, o CLR ignora o HRESULT retornado por cada retorno de chamada, exceto [ICorProfilerCallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 No registro do Microsoft Windows, um criador de perfil de código deve registrar seu objeto de modelo de objeto de componente (COM) que implementa o `ICorProfilerCallback` e `ICorProfilerCallback2` interfaces. Um criador de perfil de código assina os eventos para os quais deseja receber notificação chamando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Geralmente, isso é feito na implementação do criador de perfil do [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). O criador de perfil, em seguida, é capaz de receber a notificação de tempo de execução quando um evento está prestes a ocorrer ou se ocorreu em um processo em execução de tempo de execução.  
  
> [!NOTE]
>  O criador de perfil registra um único objeto COM. Se o criador de perfil está direcionando o .NET Framework versão 1.0 ou 1.1, que o objeto COM precisa implementar apenas os métodos de `ICorProfilerCallback`. Se ele for destinado ao .NET Framework versão 2.0 ou posterior, o objeto COM também deve implementar os métodos de `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
