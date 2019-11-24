---
title: Método ICorProfilerFunctionControl::SetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: f6e2cfe47bdd212e39549544b06bf5b11033a956
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429890"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="7c9a3-102">Método ICorProfilerFunctionControl::SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="7c9a3-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="7c9a3-103">Substitui o corpo CIL (Common Intermediate Language) do método.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c9a3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c9a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c9a3-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="7c9a3-106">[in] O tamanho total do novo CIL, incluindo o cabeçalho e quaisquer estruturas que vierem após o corpo.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="7c9a3-107">[in] Um ponteiro para o novo cabeçalho CIL.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c9a3-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7c9a3-108">Return Value</span></span>  
 <span data-ttu-id="7c9a3-109">Esse método retorna os HRESULTs específicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="7c9a3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c9a3-110">HRESULT</span></span>|<span data-ttu-id="7c9a3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c9a3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c9a3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c9a3-112">S_OK</span></span>|<span data-ttu-id="7c9a3-113">A substituição foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9a3-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c9a3-114">Remarks</span></span>  
 <span data-ttu-id="7c9a3-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="7c9a3-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="7c9a3-117">Ele pode ser alocado em qualquer heap.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-117">It can be allocated on any heap.</span></span> <span data-ttu-id="7c9a3-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span><span class="sxs-lookup"><span data-stu-id="7c9a3-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9a3-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c9a3-119">Requirements</span></span>  
 <span data-ttu-id="7c9a3-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9a3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9a3-121">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c9a3-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c9a3-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c9a3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c9a3-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9a3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9a3-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c9a3-124">See also</span></span>

- [<span data-ttu-id="7c9a3-125">Interface ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="7c9a3-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
