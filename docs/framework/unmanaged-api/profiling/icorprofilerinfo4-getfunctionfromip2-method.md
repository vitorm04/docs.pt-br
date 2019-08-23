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
ms.openlocfilehash: 8c133338ec0edac19f49d435df41e3081c486f51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948459"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="ef5ca-102">Método ICorProfilerInfo4::GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="ef5ca-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="ef5ca-103">Mapeia um ponteiro de instrução de código gerenciado para a versão recompilada do JIT de uma função.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef5ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef5ca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef5ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef5ca-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="ef5ca-106">no O ponteiro de instrução no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="ef5ca-107">fora A ID da função.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="ef5ca-108">fora A identidade da versão recompilada do JIT da função.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef5ca-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef5ca-109">Remarks</span></span>  
 <span data-ttu-id="ef5ca-110">`GetFunctionFromIP2`é semelhante a `GetFunctionFromIP`, exceto pelo fato de que ele obtém a ID recompilada de JIT em vez da ID de função da função que contém o endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef5ca-111">`GetFunctionFromIP2`pode disparar uma coleta de lixo, `GetFunctionFromIP` enquanto não vai.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="ef5ca-112">Para obter mais informações, consulte [HRESULT do CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="ef5ca-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef5ca-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef5ca-113">Requirements</span></span>  
 <span data-ttu-id="ef5ca-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef5ca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef5ca-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef5ca-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef5ca-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef5ca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef5ca-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef5ca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5ca-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef5ca-118">See also</span></span>

- [<span data-ttu-id="ef5ca-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="ef5ca-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
