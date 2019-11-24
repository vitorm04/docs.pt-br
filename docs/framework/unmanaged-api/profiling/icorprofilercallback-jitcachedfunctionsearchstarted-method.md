---
title: Método ICorProfilerCallback::JITCachedFunctionSearchStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 5d3fe6691a2d9989de002bad09c2e8f66a094f56
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448438"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="d8ffc-102">Método ICorProfilerCallback::JITCachedFunctionSearchStarted</span><span class="sxs-lookup"><span data-stu-id="d8ffc-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="d8ffc-103">Notifica o criador de perfil de que uma pesquisa foi iniciada para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="d8ffc-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ffc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8ffc-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8ffc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8ffc-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d8ffc-106">no A ID da função para a qual a pesquisa está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="d8ffc-107">[fora] `true` se o mecanismo de execução deve usar a versão em cache de uma função (se disponível); caso contrário `false`.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="d8ffc-108">Se o valor for `false`, o mecanismo de execução JIT compilará a função em vez de usar uma versão que não seja compilada por JIT.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ffc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8ffc-109">Remarks</span></span>  
 <span data-ttu-id="d8ffc-110">No .NET Framework versão 2,0, os retornos de chamada do método `JITCachedFunctionSearchStarted` e [ICorProfilerCallback:: JITCachedFunctionSearchFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) não serão feitos para todas as funções em imagens NGen regulares.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="d8ffc-111">Somente imagens NGen otimizadas para um perfil gerarão retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="d8ffc-112">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar imagens NGen otimizadas para o criador de perfil somente se pretender usar esses retornos de chamada para forçar uma função a ser compilada just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="d8ffc-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="d8ffc-113">Caso contrário, o criador de perfil deve usar uma estratégia lenta para coletar informações de função.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="d8ffc-114">Os profileres devem oferecer suporte a casos em que vários threads de um aplicativo de perfil criado chamem o mesmo método simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="d8ffc-115">Por exemplo, thread A chama `JITCachedFunctionSearchStarted` e o criador de perfil responde definindo *pbUseCachedFunction*como false para forçar a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="d8ffc-116">O thread A chama [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) e [ICorProfilerCallback:: JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8ffc-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="d8ffc-117">Agora, o thread B chama `JITCachedFunctionSearchStarted` para a mesma função.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="d8ffc-118">Embora o criador de perfil tenha declarado sua intenção de compilar a função por JIT, o criador de perfil recebe o segundo retorno de chamada, pois o thread B envia o retorno de chamada antes que o criador de perfil tenha respondido à chamada do thread a `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="d8ffc-119">A ordem na qual os threads fazem chamadas depende de como os threads são agendados.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="d8ffc-120">Quando o criador de perfil recebe retornos de chamada duplicados, ele deve definir o valor referenciado por `pbUseCachedFunction` com o mesmo valor para todos os retornos de chamada duplicados.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="d8ffc-121">Ou seja, quando `JITCachedFunctionSearchStarted` é chamado várias vezes com o mesmo valor de `functionId`, o criador de perfil deve responder o mesmo a cada vez.</span><span class="sxs-lookup"><span data-stu-id="d8ffc-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ffc-122">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d8ffc-122">Requirements</span></span>  
 <span data-ttu-id="d8ffc-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ffc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ffc-124">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d8ffc-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8ffc-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ffc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ffc-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ffc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ffc-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8ffc-127">See also</span></span>

- [<span data-ttu-id="d8ffc-128">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d8ffc-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
