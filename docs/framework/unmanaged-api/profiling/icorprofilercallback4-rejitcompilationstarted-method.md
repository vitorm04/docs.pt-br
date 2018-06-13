---
title: Método ICorProfilerCallback4::ReJITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3e21d42340378c576bfc65750fba26a257b82cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457740"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="74a08-102">Método ICorProfilerCallback4::ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="74a08-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="74a08-103">Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="74a08-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74a08-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74a08-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74a08-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="74a08-106">[in] A ID da função que o compilador JIT começou a recompilação.</span><span class="sxs-lookup"><span data-stu-id="74a08-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="74a08-107">[in] A ID de recompilação da nova versão da função.</span><span class="sxs-lookup"><span data-stu-id="74a08-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="74a08-108">[in] `true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; `false` para indicar que a bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="74a08-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="74a08-109">Um valor de `true` não prejudicar o tempo de execução, mas podem afetar os resultados da criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="74a08-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74a08-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="74a08-110">Remarks</span></span>  
 <span data-ttu-id="74a08-111">É possível receber mais de um par de `ReJITCompilationStarted` e [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) método chama para cada função devido a maneira como o tempo de execução construtores de classe de identificadores.</span><span class="sxs-lookup"><span data-stu-id="74a08-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="74a08-112">Por exemplo, o tempo de execução inicia a recompilação de um método de, mas o construtor de classe para classe B deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="74a08-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="74a08-113">Portanto, o tempo de execução recompila o construtor de classe B e o executa.</span><span class="sxs-lookup"><span data-stu-id="74a08-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="74a08-114">Durante a execução, o construtor faz uma chamada ao método A, que faz com que o método A ser recompilado novamente.</span><span class="sxs-lookup"><span data-stu-id="74a08-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="74a08-115">Nesse cenário, a recompilação de primeiro do método um é interrompida.</span><span class="sxs-lookup"><span data-stu-id="74a08-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="74a08-116">No entanto, ambos tenta recompilar o método A é relatada com eventos de recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="74a08-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="74a08-117">Criadores de perfil devem dar suporte a sequência de retornos de chamada de recompilação de JIT em casos onde dois threads simultaneamente fazem retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="74a08-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="74a08-118">Por exemplo, um thread de chamadas `ReJITCompilationStarted`; no entanto, antes de chamadas do thread A [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), chamadas de thread B [: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função do `ReJITCompilationStarted` retorno de chamada do thread A. Pode parecer que a ID de função não deve ainda ser válida porque uma chamada para [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) ainda não foi recebido pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="74a08-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="74a08-119">No entanto, nesse caso, a ID de função é válida.</span><span class="sxs-lookup"><span data-stu-id="74a08-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a08-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74a08-120">Requirements</span></span>  
 <span data-ttu-id="74a08-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74a08-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a08-122">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74a08-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74a08-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a08-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74a08-124">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74a08-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a08-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74a08-125">See Also</span></span>  
 [<span data-ttu-id="74a08-126">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="74a08-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="74a08-127">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="74a08-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="74a08-128">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="74a08-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [<span data-ttu-id="74a08-129">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="74a08-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
