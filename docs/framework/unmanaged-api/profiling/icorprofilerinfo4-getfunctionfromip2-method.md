---
title: "Método ICorProfilerInfo4::GetFunctionFromIP2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetFunctionFromIP2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f354bdc198a8060c7241a2b9bdb472bee5ed7b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="a645d-102">Método ICorProfilerInfo4::GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="a645d-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="a645d-103">Um ponteiro de instrução do código gerenciado é mapeado para a versão recompilada JIT de uma função.</span><span class="sxs-lookup"><span data-stu-id="a645d-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a645d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a645d-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a645d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a645d-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="a645d-106">[in] O ponteiro de instrução em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a645d-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="a645d-107">[out] A ID de função.</span><span class="sxs-lookup"><span data-stu-id="a645d-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="a645d-108">[out] A identidade da versão recompilada JIT da função.</span><span class="sxs-lookup"><span data-stu-id="a645d-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a645d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a645d-109">Remarks</span></span>  
 <span data-ttu-id="a645d-110">`GetFunctionFromIP2`é semelhante ao `GetFunctionFromIP`, exceto que ele obtém a ID recompilado JIT em vez da ID de função da função que contém o endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="a645d-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a645d-111">`GetFunctionFromIP2`pode disparar uma coleta de lixo, enquanto `GetFunctionFromIP` não.</span><span class="sxs-lookup"><span data-stu-id="a645d-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="a645d-112">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="a645d-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a645d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a645d-113">Requirements</span></span>  
 <span data-ttu-id="a645d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a645d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a645d-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a645d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a645d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a645d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a645d-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a645d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a645d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a645d-118">See Also</span></span>  
 [<span data-ttu-id="a645d-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a645d-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
