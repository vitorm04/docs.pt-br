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
ms.openlocfilehash: ea66474e809b3813faceef79a69dd8a639a72a3b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502789"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="e165c-102">Método ICorProfilerInfo4::GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="e165c-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="e165c-103">Mapeia um ponteiro de instrução de código gerenciado para a versão recompilada do JIT de uma função.</span><span class="sxs-lookup"><span data-stu-id="e165c-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e165c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e165c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e165c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e165c-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="e165c-106">no O ponteiro de instrução no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e165c-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="e165c-107">fora A ID da função.</span><span class="sxs-lookup"><span data-stu-id="e165c-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="e165c-108">fora A identidade da versão recompilada do JIT da função.</span><span class="sxs-lookup"><span data-stu-id="e165c-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e165c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e165c-109">Remarks</span></span>  
 <span data-ttu-id="e165c-110">`GetFunctionFromIP2`é semelhante a `GetFunctionFromIP` , exceto pelo fato de que ele obtém a ID recompilada de JIT em vez da ID de função da função que contém o endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="e165c-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e165c-111">`GetFunctionFromIP2`pode disparar uma coleta de lixo, enquanto `GetFunctionFromIP` não vai.</span><span class="sxs-lookup"><span data-stu-id="e165c-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="e165c-112">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="e165c-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e165c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e165c-113">Requirements</span></span>  
 <span data-ttu-id="e165c-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e165c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e165c-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e165c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e165c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e165c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e165c-117">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e165c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e165c-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="e165c-118">See also</span></span>

- [<span data-ttu-id="e165c-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e165c-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
