---
title: "Método ICorProfilerCallback::JITCachedFunctionSearchStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09fcdc67dc730b59b76a2da9f6ccea04800e20c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="834a0-102">Método ICorProfilerCallback::JITCachedFunctionSearchStarted</span><span class="sxs-lookup"><span data-stu-id="834a0-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="834a0-103">Notifica o criador de perfil que uma pesquisa foi iniciada por uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="834a0-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="834a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="834a0-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="834a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="834a0-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="834a0-106">[in] A ID da função para a qual a pesquisa está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="834a0-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="834a0-107">[out] `true` se o mecanismo de execução deve usar a versão armazenada em cache de uma função (se disponível); caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="834a0-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="834a0-108">Se o valor for `false`, a execução do mecanismo de JIT compila a função em vez de usar uma versão que não é compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="834a0-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="834a0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="834a0-109">Remarks</span></span>  
 <span data-ttu-id="834a0-110">No .NET Framework versão 2.0, o `JITCachedFunctionSearchStarted` e [: Jitcachedfunctionsearchfinished método](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) retornos de chamada não serão feitos para todas as funções em imagens NGen normais.</span><span class="sxs-lookup"><span data-stu-id="834a0-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="834a0-111">Somente imagens NGen otimizadas para um perfil gerará retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="834a0-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="834a0-112">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil com otimização de NGen imagens somente se pretender usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="834a0-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="834a0-113">Caso contrário, o criador de perfil deve usar uma estratégia lenta para reunir informações de função.</span><span class="sxs-lookup"><span data-stu-id="834a0-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="834a0-114">Criadores de perfil devem dar suporte a casos em que vários threads de um aplicativo de perfil estiver chamando o mesmo método simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="834a0-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="834a0-115">Por exemplo, um thread de chamadas `JITCachedFunctionSearchStarted` e o criador de perfil responde definindo *pbUseCachedFunction*como FALSE para forçar a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="834a0-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="834a0-116">Thread de um, em seguida, chama [: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) e [Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="834a0-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="834a0-117">Agora thread B chamadas `JITCachedFunctionSearchStarted` para a mesma função.</span><span class="sxs-lookup"><span data-stu-id="834a0-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="834a0-118">Mesmo que o criador de perfil declarou sua intenção de compilação JIT a função, o criador de perfil recebe o retorno de chamada segundo porque o thread B envia o retorno de chamada antes do criador de perfil respondeu a chamada do thread para `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="834a0-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="834a0-119">A ordem na qual os threads fazer chamadas depende de como os threads são agendados.</span><span class="sxs-lookup"><span data-stu-id="834a0-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="834a0-120">Quando o criador de perfil recebe retornos de chamada duplicados, ele deve definir o valor referenciado por `pbUseCachedFunction` com o mesmo valor para retornos de chamada duplicados.</span><span class="sxs-lookup"><span data-stu-id="834a0-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="834a0-121">Ou seja, quando `JITCachedFunctionSearchStarted` for chamado várias vezes com o mesmo `functionId` valor, o criador de perfil deve responder a mesma cada vez.</span><span class="sxs-lookup"><span data-stu-id="834a0-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="834a0-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="834a0-122">Requirements</span></span>  
 <span data-ttu-id="834a0-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="834a0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="834a0-124">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="834a0-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="834a0-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="834a0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="834a0-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="834a0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834a0-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="834a0-127">See Also</span></span>  
 [<span data-ttu-id="834a0-128">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="834a0-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
