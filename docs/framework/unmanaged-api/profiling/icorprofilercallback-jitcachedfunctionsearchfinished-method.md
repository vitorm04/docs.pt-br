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
ms.openlocfilehash: bea857f65081432eb3f5501c75af6d13805c76d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426242"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="1856c-102">Método ICorProfilerCallback::JITCachedFunctionSearchFinished</span><span class="sxs-lookup"><span data-stu-id="1856c-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="1856c-103">Notifica o criador de perfil de que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="1856c-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1856c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1856c-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1856c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1856c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1856c-106">no A ID da função para a qual a pesquisa foi executada.</span><span class="sxs-lookup"><span data-stu-id="1856c-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="1856c-107">no Um valor da enumeração de [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) que indica o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1856c-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1856c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1856c-108">Remarks</span></span>  
 <span data-ttu-id="1856c-109">No .NET Framework versão 2,0, os retornos de chamada [ICorProfilerCallback:: JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) e `JITCachedFunctionSearchFinished` não serão feitos para todas as funções em imagens NGen regulares.</span><span class="sxs-lookup"><span data-stu-id="1856c-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="1856c-110">Somente imagens NGen otimizadas para um criador de perfil gerarão retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="1856c-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="1856c-111">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar imagens NGen otimizadas para o criador de perfil somente se pretender usar esses retornos de chamada para forçar uma função a ser compilada just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="1856c-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="1856c-112">Caso contrário, o criador de perfil deve usar uma estratégia lenta para coletar informações de função.</span><span class="sxs-lookup"><span data-stu-id="1856c-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1856c-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1856c-113">Requirements</span></span>  
 <span data-ttu-id="1856c-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1856c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1856c-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1856c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1856c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1856c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1856c-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1856c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1856c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1856c-118">See also</span></span>

- [<span data-ttu-id="1856c-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1856c-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
