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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3550f4da497574ea5076766ad201e9431af52e4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598006"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="f8460-102">Método ICorProfilerCallback::JITCachedFunctionSearchStarted</span><span class="sxs-lookup"><span data-stu-id="f8460-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="f8460-103">Notifica o criador de perfil que uma pesquisa foi iniciada para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="f8460-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8460-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8460-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8460-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8460-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f8460-106">[in] A ID da função para o qual a pesquisa está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="f8460-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="f8460-107">[out] `true` se o mecanismo de execução deve usar a versão em cache de uma função (se disponível); caso contrário `false`.</span><span class="sxs-lookup"><span data-stu-id="f8460-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="f8460-108">Se o valor for `false`, a execução do mecanismo de JIT compila a função em vez de usar uma versão que não é compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="f8460-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8460-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8460-109">Remarks</span></span>  
 <span data-ttu-id="f8460-110">No .NET Framework versão 2.0, o `JITCachedFunctionSearchStarted` e [método ICorProfilerCallback:: Jitcachedfunctionsearchfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) retornos de chamada não serão feitos para todas as funções em imagens de NGen regulares.</span><span class="sxs-lookup"><span data-stu-id="f8460-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="f8460-111">Somente as imagens NGen otimizadas para um perfil irá gerar retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="f8460-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="f8460-112">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil otimizado as imagens NGen somente se ele pretende usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="f8460-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="f8460-113">Caso contrário, o criador de perfil deve usar uma estratégia de lenta para reunir informações de função.</span><span class="sxs-lookup"><span data-stu-id="f8460-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="f8460-114">Os criadores de perfis devem dar suporte a casos em que vários threads de um aplicativo analisado estiver chamando o mesmo método simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="f8460-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="f8460-115">Por exemplo, o thread A chama `JITCachedFunctionSearchStarted` e o criador de perfil responde definindo *pbUseCachedFunction*como FALSE para forçar a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="f8460-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="f8460-116">Thread de um, em seguida, chama [ICorProfilerCallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) e [ICorProfilerCallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8460-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="f8460-117">Agora thread B chama `JITCachedFunctionSearchStarted` para a mesma função.</span><span class="sxs-lookup"><span data-stu-id="f8460-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="f8460-118">Mesmo que o criador de perfil declarou sua intenção de JIT-compilar a função, o criador de perfil recebe o segundo retorno de chamada porque o thread B envia o retorno de chamada antes do criador de perfil tiver respondido à chamada do segmento para `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="f8460-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="f8460-119">A ordem na qual os threads de fazer chamadas depende de como os threads são agendados.</span><span class="sxs-lookup"><span data-stu-id="f8460-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="f8460-120">Quando o criador de perfil recebe duplicados retornos de chamada, ele deve definir o valor referenciado pelo `pbUseCachedFunction` com o mesmo valor para todos os retornos de chamada duplicados.</span><span class="sxs-lookup"><span data-stu-id="f8460-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="f8460-121">Ou seja, quando `JITCachedFunctionSearchStarted` é chamado várias vezes com o mesmo `functionId` valor, o criador de perfil deve responder a mesma cada vez.</span><span class="sxs-lookup"><span data-stu-id="f8460-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8460-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8460-122">Requirements</span></span>  
 <span data-ttu-id="f8460-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8460-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8460-124">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8460-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8460-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8460-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8460-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8460-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8460-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8460-127">See also</span></span>

- [<span data-ttu-id="f8460-128">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f8460-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
