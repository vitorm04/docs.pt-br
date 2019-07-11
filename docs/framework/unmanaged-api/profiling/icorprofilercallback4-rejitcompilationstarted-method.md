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
ms.openlocfilehash: 58293929b576493d3751f9ce30ba00cec92e180c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758172"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="ae557-102">Método ICorProfilerCallback4::ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="ae557-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="ae557-103">Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="ae557-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae557-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae557-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae557-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae557-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ae557-106">[in] A ID da função que o compilador JIT começou a recompilação.</span><span class="sxs-lookup"><span data-stu-id="ae557-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="ae557-107">[in] A ID de recompilação da nova versão da função.</span><span class="sxs-lookup"><span data-stu-id="ae557-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="ae557-108">[in] `true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae557-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="ae557-109">Um valor de `true` não prejudicará o tempo de execução, mas podem afetar os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="ae557-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae557-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae557-110">Remarks</span></span>  
 <span data-ttu-id="ae557-111">É possível receber mais de um par de `ReJITCompilationStarted` e [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) método chama para cada função devido à maneira o tempo de execução lida com construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="ae557-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="ae557-112">Por exemplo, o tempo de execução começa a recompilar um método de um, mas o construtor de classe para classe B precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="ae557-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="ae557-113">Portanto, o tempo de execução recompila o construtor da classe B e o executa.</span><span class="sxs-lookup"><span data-stu-id="ae557-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="ae557-114">Enquanto o construtor é executado, ele faz uma chamada ao método A, que faz com que o método A ser recompilado novamente.</span><span class="sxs-lookup"><span data-stu-id="ae557-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="ae557-115">Nesse cenário, a primeira recompilação de um método de é interrompida.</span><span class="sxs-lookup"><span data-stu-id="ae557-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="ae557-116">No entanto, ambas tentará recompilar A é relatada com eventos de recompilação JIT do método.</span><span class="sxs-lookup"><span data-stu-id="ae557-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="ae557-117">Os criadores de perfis devem dar suporte a sequência de retornos de chamada de recompilação JIT em casos em que dois threads simultaneamente fazendo retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="ae557-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="ae557-118">Por exemplo, o thread A chama `ReJITCompilationStarted`; no entanto, antes de chamadas do thread A [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), o thread B chama [ICorProfilerCallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função do `ReJITCompilationStarted` retorno de chamada para o thread A. Pode parecer que a ID de função não deve ainda ser válida porque uma chamada para [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) ainda não foi recebido pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="ae557-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="ae557-119">No entanto, nesse caso, a ID de função é válida.</span><span class="sxs-lookup"><span data-stu-id="ae557-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae557-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae557-120">Requirements</span></span>  
 <span data-ttu-id="ae557-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae557-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae557-122">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae557-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae557-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae557-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae557-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae557-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae557-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae557-125">See also</span></span>

- [<span data-ttu-id="ae557-126">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ae557-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ae557-127">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="ae557-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="ae557-128">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="ae557-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="ae557-129">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="ae557-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
