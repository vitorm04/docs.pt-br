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
ms.openlocfilehash: 6e340fa08800f31d36e6cfb280cac847a4fca548
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499344"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="902f9-102">Método ICorProfilerCallback4::ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="902f9-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="902f9-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="902f9-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="902f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="902f9-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="902f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="902f9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="902f9-106">no A ID da função que o compilador JIT começou a recompilar.</span><span class="sxs-lookup"><span data-stu-id="902f9-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="902f9-107">no A ID de recompilação da nova versão da função.</span><span class="sxs-lookup"><span data-stu-id="902f9-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="902f9-108">[in] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o thread de chamada retornar desse retorno de chamada; `false`para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="902f9-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="902f9-109">Um valor de não `true` danifica o tempo de execução, mas pode afetar os resultados da criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="902f9-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="902f9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="902f9-110">Remarks</span></span>  
 <span data-ttu-id="902f9-111">É possível receber mais de um par de chamadas de `ReJITCompilationStarted` método e [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução manipula construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="902f9-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="902f9-112">Por exemplo, o tempo de execução começa a recompilar o método A, mas o construtor de classe para a classe B precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="902f9-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="902f9-113">Portanto, o tempo de execução recompila o construtor para a classe B e o executa.</span><span class="sxs-lookup"><span data-stu-id="902f9-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="902f9-114">Enquanto o Construtor está em execução, ele faz uma chamada para o método A, o que faz com que o método A seja recompilado novamente.</span><span class="sxs-lookup"><span data-stu-id="902f9-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="902f9-115">Nesse cenário, a primeira recompilação do método A é interrompida.</span><span class="sxs-lookup"><span data-stu-id="902f9-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="902f9-116">No entanto, ambas as tentativas de recompilar o método A são relatadas com eventos de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="902f9-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="902f9-117">Os profileres devem dar suporte à sequência de retornos de chamada de recompilação JIT em casos em que dois threads realizam simultaneamente retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="902f9-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="902f9-118">Por exemplo, thread A chama `ReJITCompilationStarted` ; no entanto, antes de thread a chamar [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B chama [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função do `ReJITCompilationStarted` retorno de chamada para o thread A. Pode parecer que a ID da função ainda não deve ser válida porque uma chamada para [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) ainda não tinha sido recebida pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="902f9-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="902f9-119">No entanto, nesse caso, a ID da função é válida.</span><span class="sxs-lookup"><span data-stu-id="902f9-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="902f9-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="902f9-120">Requirements</span></span>  
 <span data-ttu-id="902f9-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="902f9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="902f9-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="902f9-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="902f9-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="902f9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="902f9-124">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="902f9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902f9-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="902f9-125">See also</span></span>

- [<span data-ttu-id="902f9-126">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="902f9-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="902f9-127">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="902f9-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="902f9-128">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="902f9-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="902f9-129">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="902f9-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
