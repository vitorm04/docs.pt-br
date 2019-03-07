---
title: Método ICorProfilerInfo4::GetFunctionFromIP2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51f8768fc3cd73f0fd5bdb84842af03b900fafdf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495341"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="434b6-102">Método ICorProfilerInfo4::GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="434b6-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="434b6-103">Mapeia um ponteiro de instrução de código gerenciado para a versão de uma função recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="434b6-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="434b6-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="434b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="434b6-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="434b6-106">[in] O ponteiro de instrução em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="434b6-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="434b6-107">[out] ID da função.</span><span class="sxs-lookup"><span data-stu-id="434b6-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="434b6-108">[out] A identidade da versão da função recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="434b6-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="434b6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="434b6-109">Remarks</span></span>  
 <span data-ttu-id="434b6-110">`GetFunctionFromIP2` é semelhante ao `GetFunctionFromIP`, exceto que ele obtém a ID recompilado por JIT em vez da ID de função da função que contém o endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="434b6-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="434b6-111">`GetFunctionFromIP2` pode disparar uma coleta de lixo, ao passo que `GetFunctionFromIP` será não.</span><span class="sxs-lookup"><span data-stu-id="434b6-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="434b6-112">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="434b6-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="434b6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="434b6-113">Requirements</span></span>  
 <span data-ttu-id="434b6-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="434b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="434b6-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="434b6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="434b6-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="434b6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="434b6-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="434b6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434b6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="434b6-118">See also</span></span>
- [<span data-ttu-id="434b6-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="434b6-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
