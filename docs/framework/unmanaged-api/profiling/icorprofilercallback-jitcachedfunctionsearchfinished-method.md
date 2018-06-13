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
ms.openlocfilehash: 89c7b0fe0f3ade3f57aa50b100bc9b4ecc904a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451991"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="0261e-102">Método ICorProfilerCallback::JITCachedFunctionSearchFinished</span><span class="sxs-lookup"><span data-stu-id="0261e-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="0261e-103">Notifica o criador de perfil que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="0261e-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0261e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0261e-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0261e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0261e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0261e-106">[in] A ID da função para a qual a pesquisa foi realizada.</span><span class="sxs-lookup"><span data-stu-id="0261e-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="0261e-107">[in] Um valor de [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeração que indica o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0261e-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0261e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0261e-108">Remarks</span></span>  
 <span data-ttu-id="0261e-109">No .NET Framework versão 2.0, o [: Jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) e `JITCachedFunctionSearchFinished` retornos de chamada não serão feitos para todas as funções em imagens NGen normais.</span><span class="sxs-lookup"><span data-stu-id="0261e-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="0261e-110">Somente imagens NGen otimizadas para um criador de perfil irá gerar retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="0261e-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="0261e-111">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil com otimização de NGen imagens somente se pretender usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="0261e-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="0261e-112">Caso contrário, o criador de perfil deve usar uma estratégia lenta para reunir informações de função.</span><span class="sxs-lookup"><span data-stu-id="0261e-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0261e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0261e-113">Requirements</span></span>  
 <span data-ttu-id="0261e-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0261e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0261e-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0261e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0261e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0261e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0261e-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0261e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0261e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0261e-118">See Also</span></span>  
 [<span data-ttu-id="0261e-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0261e-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
