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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177089"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="612a2-102">Método ICorProfilerCallback4::ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="612a2-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="612a2-103">Notifica o profiler de que o compilador just-in-time (JIT) começou a recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="612a2-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="612a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="612a2-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="612a2-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="612a2-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="612a2-106">[em] O ID da função que o compilador JIT começou a recompilar.</span><span class="sxs-lookup"><span data-stu-id="612a2-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="612a2-107">[em] A iD de recompilação da nova versão da função.</span><span class="sxs-lookup"><span data-stu-id="612a2-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="612a2-108">[em] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o retorno do segmento de chamada a partir deste retorno de chamada; `false` para indicar que o bloqueio não afetará o funcionamento do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="612a2-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="612a2-109">Um valor `true` de não prejudica o tempo de execução, mas pode afetar os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="612a2-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="612a2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="612a2-110">Remarks</span></span>  
 <span data-ttu-id="612a2-111">É possível receber mais de `ReJITCompilationStarted` um par de chamadas do método [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução lida com construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="612a2-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="612a2-112">Por exemplo, o tempo de execução começa a recompilar o método A, mas o construtor de classe para a classe B precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="612a2-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="612a2-113">Portanto, o tempo de execução recompila o construtor para a classe B e executa-o.</span><span class="sxs-lookup"><span data-stu-id="612a2-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="612a2-114">Enquanto o construtor está em execução, ele faz uma chamada para o método A, que faz com que o método A seja recompilado novamente.</span><span class="sxs-lookup"><span data-stu-id="612a2-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="612a2-115">Neste cenário, a primeira recompilação do método A é interrompida.</span><span class="sxs-lookup"><span data-stu-id="612a2-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="612a2-116">No entanto, ambas as tentativas de recompilação do método A são relatadas com eventos de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="612a2-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="612a2-117">Os profilers devem suportar a seqüência de recompilação de retornos de jit nos casos em que dois segmentos estão simultaneamente fazendo retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="612a2-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="612a2-118">Por exemplo, chamadas `ReJITCompilationStarted`de thread A; no entanto, antes de thread A chama [ReJITCompilationFinished,](icorprofilercallback4-rejitcompilationfinished-method.md)o thread B chama [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) com o ID de função do retorno de chamada para o `ReJITCompilationStarted` segmento A. Pode parecer que o ID da função ainda não deve ser válido porque uma chamada para [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) ainda não havia sido recebida pelo profiler.</span><span class="sxs-lookup"><span data-stu-id="612a2-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="612a2-119">No entanto, neste caso, o ID da função é válido.</span><span class="sxs-lookup"><span data-stu-id="612a2-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="612a2-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="612a2-120">Requirements</span></span>  
 <span data-ttu-id="612a2-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="612a2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="612a2-122">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="612a2-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="612a2-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="612a2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="612a2-124">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="612a2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612a2-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="612a2-125">See also</span></span>

- [<span data-ttu-id="612a2-126">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="612a2-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="612a2-127">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="612a2-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="612a2-128">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="612a2-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="612a2-129">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="612a2-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
