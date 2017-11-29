---
title: "Método ICorProfilerCallback::JITCachedFunctionSearchFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ffbe331399334d179cf8325e7d9e6773b5bf7012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="d5cb3-102">Método ICorProfilerCallback::JITCachedFunctionSearchFinished</span><span class="sxs-lookup"><span data-stu-id="d5cb3-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="d5cb3-103">Notifica o criador de perfil que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="d5cb3-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5cb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5cb3-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5cb3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5cb3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d5cb3-106">[in] A ID da função para a qual a pesquisa foi realizada.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="d5cb3-107">[in] Um valor de [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeração que indica o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5cb3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5cb3-108">Remarks</span></span>  
 <span data-ttu-id="d5cb3-109">No .NET Framework versão 2.0, o [: Jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) e `JITCachedFunctionSearchFinished` retornos de chamada não serão feitos para todas as funções em imagens NGen normais.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="d5cb3-110">Somente imagens NGen otimizadas para um criador de perfil irá gerar retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="d5cb3-111">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil com otimização de NGen imagens somente se pretender usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="d5cb3-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="d5cb3-112">Caso contrário, o criador de perfil deve usar uma estratégia lenta para reunir informações de função.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cb3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5cb3-113">Requirements</span></span>  
 <span data-ttu-id="d5cb3-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5cb3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cb3-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5cb3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5cb3-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5cb3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5cb3-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cb3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5cb3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5cb3-118">See Also</span></span>  
 [<span data-ttu-id="d5cb3-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d5cb3-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
