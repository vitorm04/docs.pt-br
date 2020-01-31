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
ms.openlocfilehash: 8ad04a7a6705b961686317c9473b885fb90676ce
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861912"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="f4284-102">Método ICorProfilerInfo4::GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="f4284-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="f4284-103">Mapeia um ponteiro de instrução de código gerenciado para a versão recompilada do JIT de uma função.</span><span class="sxs-lookup"><span data-stu-id="f4284-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4284-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4284-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4284-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4284-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="f4284-106">no O ponteiro de instrução no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f4284-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="f4284-107">fora A ID da função.</span><span class="sxs-lookup"><span data-stu-id="f4284-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="f4284-108">fora A identidade da versão recompilada do JIT da função.</span><span class="sxs-lookup"><span data-stu-id="f4284-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4284-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4284-109">Remarks</span></span>  
 <span data-ttu-id="f4284-110">`GetFunctionFromIP2` é semelhante a `GetFunctionFromIP`, exceto pelo fato de que ele obtém a ID recompilada por JIT em vez da ID de função da função que contém o endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="f4284-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4284-111">`GetFunctionFromIP2` pode disparar uma coleta de lixo, enquanto `GetFunctionFromIP` não vai.</span><span class="sxs-lookup"><span data-stu-id="f4284-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="f4284-112">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="f4284-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4284-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="f4284-113">Requirements</span></span>  
 <span data-ttu-id="f4284-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4284-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4284-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f4284-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4284-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4284-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4284-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4284-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4284-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="f4284-118">See also</span></span>

- [<span data-ttu-id="f4284-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f4284-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
