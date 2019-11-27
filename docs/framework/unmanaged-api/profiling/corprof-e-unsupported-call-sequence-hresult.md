---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: 4d835f749a33d21a13be307e1524671e36496899
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440833"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
O CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT foi introduzido na versão .NET Framework 2,0. O .NET Framework 4 retorna esse HRESULT em dois cenários:  
  
- Quando um criador de perfil de seqüestro redefine forçosamente o contexto de registro de um thread em um momento arbitrário para que o thread tente acessar as estruturas que estão em um estado inconsistente.  
  
- Quando um criador de perfil tenta chamar um método informativo que dispara a coleta de lixo de um método de retorno de chamada que proíbe a coleta de lixo.  
  
 Esses dois cenários são discutidos nas seções a seguir.  
  
## <a name="hijacking-profilers"></a>Profileres de seqüestro  
 (Esse cenário é basicamente um problema com os profileres de seqüestro, embora haja casos em que os profileres de não-seqüestro possam ver esse HRESULT.)  
  
 Nesse cenário, um criador de perfil de seqüestro redefine forçosamente o contexto de registro de um thread em um momento arbitrário para que o thread possa inserir o código do criador de perfil ou inserir novamente o Common Language Runtime (CLR) por meio de um método [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .  
  
 Muitas das IDs que a API de criação de perfil fornece aponta para estruturas de dados no CLR. Muitas chamadas de `ICorProfilerInfo` simplesmente lêem informações dessas estruturas de dados e as transmitem de volta. No entanto, o CLR pode alterar as coisas nessas estruturas à medida que é executado e pode usar bloqueios para fazer isso. Suponha que o CLR já esteja mantendo (ou tentando adquirir) um bloqueio no momento em que o criador de perfil seqüestrar o thread. Se o thread inserir novamente o CLR e tentar obter mais bloqueios ou inspecionar estruturas que estavam no processo de ser modificado, essas estruturas poderão estar em um estado inconsistente. Deadlocks e violações de acesso podem ocorrer facilmente nessas situações.  
  
 Em geral, quando um profiler sem seqüestro executa o código dentro de um método [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e chama um método de `ICorProfilerInfo` com parâmetros válidos, ele não deve ter um deadlock ou receber uma violação de acesso. Por exemplo, o código do criador de perfil que é executado dentro do método [ICorProfilerCallback:: ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) pode solicitar informações sobre a classe chamando o método [ICorProfilerInfo2:: GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) . O código pode receber um CORPROF_E_DATAINCOMPLETE HRESULT para indicar que as informações estão indisponíveis; no entanto, ele não causará deadlock ou receberá uma violação de acesso. Essa classe de chamadas em `ICorProfilerInfo` é chamada de Synchronous, pois são feitas de um método `ICorProfilerCallback`.  
  
 No entanto, um thread gerenciado que executa o código que não está dentro de um método de `ICorProfilerCallback` é considerado como tendo uma chamada assíncrona. No .NET Framework versão 1, era difícil determinar o que pode acontecer em uma chamada assíncrona. A chamada pode travar, falhar ou dar uma resposta inválida. O .NET Framework versão 2,0 introduziu algumas verificações simples para ajudá-lo a evitar esse problema. No .NET Framework 2,0, se você chamar uma função de `ICorProfilerInfo` não segura de forma assíncrona, ela falhará com um HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE.  
  
 Em geral, as chamadas assíncronas não são seguras. No entanto, os métodos a seguir são seguros e oferecem suporte especificamente a chamadas assíncronas:  
  
- [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Para obter informações adicionais, consulte a entrada [por que temos CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://go.microsoft.com/fwlink/?LinkId=169156) no blog da API de criação de perfil do CLR.  
  
## <a name="triggering-garbage-collections"></a>Disparando coleções de lixo  
 Esse cenário envolve um criador de perfil que está sendo executado dentro de um método de retorno de chamada (por exemplo, um dos métodos `ICorProfilerCallback`) que proíbe a coleta de lixo. Se o criador de perfil tentar chamar um método informativo (por exemplo, um método na interface `ICorProfilerInfo`) que possa disparar uma coleta de lixo, o método informativo falhará com uma CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 A tabela a seguir exibe os métodos de retorno de chamada que proíbem coletas de lixo e métodos informativos que podem disparar coletas de lixo. Se o criador de perfil for executado dentro de um dos métodos de retorno de chamada listados e chamar um dos métodos informativos listados, esse método informativo falhará com um CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Métodos de retorno de chamada que proíbem coletas de lixo|Métodos informativos que disparam coletas de lixo|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [Objectreferências](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
