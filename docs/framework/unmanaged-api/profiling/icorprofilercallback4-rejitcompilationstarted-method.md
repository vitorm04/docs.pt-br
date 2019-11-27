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
ms.openlocfilehash: 074b0b11a822d2b8bcb9588484557e3e5eba69dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430200"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="40f12-102">Método ICorProfilerCallback4::ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="40f12-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="40f12-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="40f12-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40f12-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40f12-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40f12-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="40f12-106">no A ID da função que o compilador JIT começou a recompilar.</span><span class="sxs-lookup"><span data-stu-id="40f12-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="40f12-107">no A ID de recompilação da nova versão da função.</span><span class="sxs-lookup"><span data-stu-id="40f12-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="40f12-108">[in] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="40f12-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="40f12-109">Um valor de `true` não danifica o tempo de execução, mas pode afetar os resultados da criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="40f12-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f12-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="40f12-110">Remarks</span></span>  
 <span data-ttu-id="40f12-111">É possível receber mais de um par de chamadas de método `ReJITCompilationStarted` e [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução manipula construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="40f12-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="40f12-112">Por exemplo, o tempo de execução começa a recompilar o método A, mas o construtor de classe para a classe B precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="40f12-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="40f12-113">Portanto, o tempo de execução recompila o construtor para a classe B e o executa.</span><span class="sxs-lookup"><span data-stu-id="40f12-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="40f12-114">Enquanto o Construtor está em execução, ele faz uma chamada para o método A, o que faz com que o método A seja recompilado novamente.</span><span class="sxs-lookup"><span data-stu-id="40f12-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="40f12-115">Nesse cenário, a primeira recompilação do método A é interrompida.</span><span class="sxs-lookup"><span data-stu-id="40f12-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="40f12-116">No entanto, ambas as tentativas de recompilar o método A são relatadas com eventos de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="40f12-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="40f12-117">Os profileres devem dar suporte à sequência de retornos de chamada de recompilação JIT em casos em que dois threads realizam simultaneamente retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="40f12-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="40f12-118">Por exemplo, thread A chama `ReJITCompilationStarted`; no entanto, antes do thread A chamar [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B chama [ICorProfilerCallback:: EXCEPTIONSEARCHFUNCTIONENTER](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID da função do retorno de chamada `ReJITCompilationStarted` para o thread A. Pode parecer que a ID da função ainda não deve ser válida porque uma chamada para [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) ainda não tinha sido recebida pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="40f12-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="40f12-119">No entanto, nesse caso, a ID da função é válida.</span><span class="sxs-lookup"><span data-stu-id="40f12-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f12-120">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="40f12-120">Requirements</span></span>  
 <span data-ttu-id="40f12-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f12-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f12-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="40f12-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40f12-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40f12-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40f12-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f12-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f12-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40f12-125">See also</span></span>

- [<span data-ttu-id="40f12-126">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="40f12-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="40f12-127">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="40f12-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="40f12-128">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="40f12-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="40f12-129">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="40f12-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
