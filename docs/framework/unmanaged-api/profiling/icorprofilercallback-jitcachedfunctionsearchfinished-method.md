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
ms.openlocfilehash: 6efc9d407bb95f75a79252b2dfad85b396d2164a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500072"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="30b5b-102">Método ICorProfilerCallback::JITCachedFunctionSearchFinished</span><span class="sxs-lookup"><span data-stu-id="30b5b-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="30b5b-103">Notifica o criador de perfil de que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="30b5b-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30b5b-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30b5b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30b5b-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="30b5b-106">\[in] a ID da função para a qual a pesquisa foi executada.</span><span class="sxs-lookup"><span data-stu-id="30b5b-106">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="30b5b-107">\[in] um valor da enumeração [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) que indica o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="30b5b-107">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="30b5b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="30b5b-108">Remarks</span></span>  
 <span data-ttu-id="30b5b-109">No .NET Framework versão 2,0, [ICorProfilerCallback:: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) e `JITCachedFunctionSearchFinished` retornos de chamada não serão feitos para todas as funções em imagens NGen regulares.</span><span class="sxs-lookup"><span data-stu-id="30b5b-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="30b5b-110">Somente imagens NGen otimizadas para um criador de perfil gerarão retornos de chamada para todas as funções na imagem.</span><span class="sxs-lookup"><span data-stu-id="30b5b-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="30b5b-111">No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar imagens NGen otimizadas para o criador de perfil somente se pretender usar esses retornos de chamada para forçar uma função a ser compilada just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="30b5b-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="30b5b-112">Caso contrário, o criador de perfil deve usar uma estratégia lenta para coletar informações de função.</span><span class="sxs-lookup"><span data-stu-id="30b5b-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b5b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30b5b-113">Requirements</span></span>  
 <span data-ttu-id="30b5b-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b5b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b5b-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="30b5b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30b5b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30b5b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30b5b-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b5b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b5b-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="30b5b-118">See also</span></span>

- [<span data-ttu-id="30b5b-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="30b5b-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
