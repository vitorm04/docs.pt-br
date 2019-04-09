---
title: Enumeração COR_PRF_MONITOR
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb39eb768069a737f3f89c771bf02fd6bc0c3b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102395"
---
# <a name="corprfmonitor-enumeration"></a>Enumeração COR_PRF_MONITOR
Contém valores usados para especificar comportamentos, recursos ou eventos que o criador de perfis deseja assinar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a>Membros  
 As seções a seguir listam `COR_PRF_MONITOR` membros de enumeração por categoria. As categorias são:  
  
-   [Nenhum conjunto de sinalizadores](#None)  
  
-   [Sinalizadores de retorno de chamada](#Callback)  
  
-   [Sinalizadores de habilitação de recurso](#Feature)  
  
-   [Sinalizadores de configuração](#Config)  
  
-   [Sinalizadores compostos](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Nenhum conjunto de sinalizadores  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Nenhum sinalizador está definido.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Sinalizadores de retorno de chamada  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Habilita todos os eventos de retorno de chamada.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Controles de `AppDomainCreation*` e `AppDomainShutdown*` retornos de chamada na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Controles de `AssemblyLoad*` e `AssemblyUnload*` retornos de chamada na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Controles de `JITCachedFunctionSearch*` retornos de chamada na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.<br /><br /> O comportamento deste sinalizador é alterado no .NET Framework versão 2.0.|  
|`COR_PRF_MONITOR_CCW`|Controles de `COMClassicVTable*` retornos de chamada na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Controles de `ClassLoad*` e `ClassUnload*` retornos de chamada na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Controles de `ExceptionCLRCatcher*` retornos de chamada na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Controles de [UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) e [ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) retornos de chamada no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Controles de `FunctionEnter*`, `FunctionLeave*`, e `FunctionTailCall*` [funções estáticas globais de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Controles de [ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) retorno de chamada e o `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, e `ExceptionCatcher*` retornos de chamada no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Controles de [FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) retorno de chamada a [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_GC`|Controles de [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md), [ SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md), [ RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md), e [FinalizeableObjectQueued ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) retornos de chamada no `ICorProfilerCallback*` interfaces.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Controles de `JITCompilation*`, [JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md), e [JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) retornos de chamada no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Controles de `ModuleLoad*`, `ModuleUnload*`, e [ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) retornos de chamada no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Controles de [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) retorno de chamada a [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_REMOTING`|Controles de `Remoting*` retornos de chamada na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Controla se os retornos de chamada `Remoting*` vão monitorar ou não os eventos de forma assíncrona.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Controla se um cookie é passado para os retornos de chamada `Remoting*`.|  
|`COR_PRF_MONITOR_SUSPENDS`|Controles de `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md), e [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) retornos de chamada no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.|  
|`COR_PRF_MONITOR_THREADS`|Controles de [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md), e [ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) retornos de chamada no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfaces.|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Sinalizadores de habilitação de recurso  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Permite a recuperação de um exata `ClassID` para uma função genérica, chamando o [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método com um `COR_PRF_FRAME_INFO` valor retornado pela [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) retorno de chamada.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Habilita o rastreamento de argumento usando o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) retorno de chamada ou o [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) retorno de chamada e o [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) método.|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Habilita o rastreamento de valores retornados usando o [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) retorno de chamada ou o [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) retorno de chamada e [GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) método.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Preterido.<br /><br /> Não tem suporte no processo de depuração. Este sinalizador não tem efeito.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Preterido.<br /><br /> Permite que o criador de perfil obtenha mapas IL para nativo usando [GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md). A partir do .NET Framework 2.0, o tempo de execução sempre acompanha os mapas IL para nativo, portanto, esse sinalizador é sempre considerado como definido.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informa o tempo de execução que o criador de perfil pode desejar para notificações de alocação do objeto. Este sinalizador deve ser definido durante a inicialização. Ele permite que o criador de perfil Use posteriormente o `COR_PRF_MONITOR_OBJECT_ALLOCATED` sinalizador para receber [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) retornos de chamada.|  
|`COR_PRF_ENABLE_REJIT`|Permite chamadas para o [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) e [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) métodos. O criador de perfil deve definir este sinalizador na inicialização.  Se o criador de perfil especificar este sinalizador, também deverá especificar `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Permite chamadas para o [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Sinalizadores de configuração  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Impede o carregamento de todas as imagens nativas (incluindo imagens aprimoradas do criador de perfil).  Se este sinalizador e o sinalizador `COR_PRF_USE_PROFILE_IMAGES` estiverem especificados, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` será usado.|  
|`COR_PRF_DISABLE_INLINING`|Desabilita todas as conexões embutidas.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Desabilita todas as otimizações de código.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Desabilita verificações de transparência de segurança que normalmente são feitas durante a compilação JIT (Just-in-Time) e o carregamento de classe para os conjuntos de confiança total. Isso pode facilitar a execução de instrumentação.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Faz com que a imagem nativa procure imagens aprimoradas para o criador de perfil. Se nenhuma imagem aprimorada para o criador de perfil for encontrada para determinada montagem, o Common Language Runtime (CRL) retornará ao JIT para esse assembly. Se este sinalizador e o sinalizador `COR_PRF_DISABLE_ALL_NGEN_IMAGES` estiverem especificados, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` será usado.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Sinalizadores compostos  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_ALL`|Representa todos os valores de sinalizador `COR_PRF_MONITOR`.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Representa todos os sinalizadores `COR_PRF_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução. A seção de sintaxe indica os sinalizadores individuais que estão presentes nesta bitmask.|  
|`COR_PRF_MONITOR_ALL`|Habilita todos os eventos de retorno de chamada.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Representa todos os sinalizadores `COR_PRF_MONITOR` que podem ser definidos apenas durante a inicialização. A tentativa de alterar qualquer um desses sinalizadores após a inicialização retorna um valor `HRESULT` que indica falha.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Representa todos os sinalizadores `COR_PRF_MONITOR` que necessitam de imagens aprimoradas por perfil.|  
  
## <a name="remarks"></a>Comentários  
 Um `COR_PRF_MONITOR` valor é usado com o [ICorProfilerInfo:: Geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) e [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) métodos para definir as notificações de eventos que o common language runtime faz para o criador de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [Método GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [Método SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
