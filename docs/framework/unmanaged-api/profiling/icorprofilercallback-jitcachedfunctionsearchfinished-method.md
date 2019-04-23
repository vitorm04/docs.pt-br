---
title: Método ICorProfilerCallback::JITCachedFunctionSearchFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0e78e10f092bce1c8f7762362f02b7a403c86a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122935"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="a400d-102">Método ICorProfilerCallback::JITCachedFunctionSearchFinished</span><span class="sxs-lookup"><span data-stu-id="a400d-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="a400d-103">Notifica o criador de perfil que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="a400d-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a400d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a400d-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a400d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a400d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a400d-106">[in] A ID da função para o qual a pesquisa foi realizada.</span><span class="sxs-lookup"><span data-stu-id="a400d-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="a400d-107">[in] Um valor igual a [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeração que indica o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a400d-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a400d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a400d-108">Remarks</span></span>  
 <span data-ttu-id="a400d-109">No .NET Framework versão 2.0, o [ICorProfilerCallback:: Jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) e `JITCachedFunctionSearchFinished` retornos de chamada não serão feitos para todas as funções em imagens de NGen regulares.</span><span class="sxs-lookup"><span data-stu-id="a400d-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="a400d-110">Somente as imagens NGen otimizadas para um criador de perfil irá gerar retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="a400d-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="a400d-111">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil otimizado as imagens NGen somente se ele pretende usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="a400d-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="a400d-112">Caso contrário, o criador de perfil deve usar uma estratégia de lenta para reunir informações de função.</span><span class="sxs-lookup"><span data-stu-id="a400d-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a400d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a400d-113">Requirements</span></span>  
 <span data-ttu-id="a400d-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a400d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a400d-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a400d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a400d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a400d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a400d-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a400d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a400d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a400d-118">See also</span></span>

- [<span data-ttu-id="a400d-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a400d-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
