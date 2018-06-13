---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cce181037ee4f4db3a828f98cc3e07dfb45aff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461624"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT foi introduzido no .NET Framework versão 2.0. O [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] retorna esse HRESULT em dois cenários:  
  
-   Quando um criador de perfil sequestro de modo forçado redefine um thread registre contexto em um momento arbitrário para que o thread tenta acessar estruturas que estão em um estado inconsistente.  
  
-   Quando um criador de perfil tenta chamar um método de informação que dispara a coleta de lixo de um método de retorno de chamada que proíbe a coleta de lixo.  
  
 Esses dois cenários são discutidos nas seções a seguir.  
  
## <a name="hijacking-profilers"></a>Sequestro de criadores de perfil  
 (Esse cenário é basicamente um problema com a captura criadores de perfis, apesar de haver casos em que criadores de perfil sequestro de não podem ver esse HRESULT.)  
  
 Nesse cenário, um criador de perfil sequestro de forçar redefine o contexto de registro do thread em um momento arbitrário para que o thread possa inserir o código de criador de perfil ou insira novamente o common language runtime (CLR) por meio de um [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) método.  
  
 Muitas das IDs que a API de criação de perfil fornece ponto para estruturas de dados no CLR. Muitos `ICorProfilerInfo` chamadas simplesmente ler as informações dessas estruturas de dados e passá-las novamente. No entanto, o CLR pode alterar coisas essas estruturas de como ele é executado, e ele pode usar bloqueios para fazer isso. Suponha que o CLR foi já mantendo (ou a tentativa de adquirir) um bloqueio no momento em que o criador de perfil apoderar o thread. Se o thread reinserido CLR e tenta use mais bloqueios ou inspecionar estruturas que estavam no processo que está sendo modificado, essas estruturas podem estar em um estado inconsistente. Violações de acesso e deadlocks podem ocorrer facilmente em tais situações.  
  
 Em geral, quando um criador de perfil sequestro não executa o código dentro de um [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) método e chama um `ICorProfilerInfo` método com parâmetros válidos, ele não deve deadlock ou recebe uma violação de acesso. Por exemplo, o código de criador de perfil que é executado dentro do [Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) método pode solicitar informações sobre a classe chamando o [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) método. O código pode receber um HRESULT CORPROF_E_DATAINCOMPLETE para indicar que a informação está disponível; No entanto, ele não será um deadlock ou recebe uma violação de acesso. Essa classe de chamadas em `ICorProfilerInfo` são chamadas síncronas, porque eles são feitos de um `ICorProfilerCallback` método.  
  
 No entanto, um thread gerenciado que executa o código que não está contido em um `ICorProfilerCallback` método é considerado para estar fazendo uma chamada assíncrona. No .NET Framework versão 1, foi difícil determinar o que pode ocorrer em uma chamada assíncrona. A chamada foi um deadlock, falhas ou dar uma resposta inválida. O .NET Framework versão 2.0 introduziu algumas verificações simples para ajudá-lo a evitar esse problema. No .NET Framework 2.0, se você chamar um unsafe `ICorProfilerInfo` funcionar de forma assíncrona, ele falhará com um CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Em geral, as chamadas assíncronas não são seguras. No entanto, os métodos a seguir são seguros e suportam a chamadas assíncronas especificamente:  
  
-   [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
-   [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
-   [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
-   [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
-   [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
-   [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
-   [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
-   [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
-   [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
-   [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
-   [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
-   [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
-   [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
-   [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
-   [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
-   [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Para obter informações adicionais, consulte a entrada [por que temos CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](http://go.microsoft.com/fwlink/?LinkId=169156) no blog de API de criação de perfil CLR.  
  
## <a name="triggering-garbage-collections"></a>Disparo coletas de lixo  
 Este cenário envolve um criador de perfil que está em execução dentro de um método de retorno de chamada (por exemplo, uma da `ICorProfilerCallback` métodos) que não permite a coleta de lixo. Se o criador de perfil tentar chamar um método de informação (por exemplo, um método no `ICorProfilerInfo` interface) que podem disparar uma coleta de lixo, o método informativo falhará com um CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 A tabela a seguir exibe os métodos de retorno de chamada que proíbam coletas de lixo e informativos métodos que podem disparar coletas de lixo. Se o criador de perfil é executado dentro de um dos métodos de retorno de chamada listados e chama um dos métodos listados informativos, esse método informativo falhará com um CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Métodos de retorno de chamada que proíbam coletas de lixo|Métodos de informação que disparam coletas de lixo|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
