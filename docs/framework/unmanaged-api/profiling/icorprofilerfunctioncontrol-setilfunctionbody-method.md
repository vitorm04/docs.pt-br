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
ms.openlocfilehash: bebc0cf6ac7912ea3a6641e0c729b759e865dac3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864655"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="dfe0f-102">Método ICorProfilerFunctionControl::SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="dfe0f-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="dfe0f-103">Substitui o corpo CIL (Common Intermediate Language) do método.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfe0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfe0f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfe0f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dfe0f-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="dfe0f-106">[in] O tamanho total do novo CIL, incluindo o cabeçalho e quaisquer estruturas que vierem após o corpo.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="dfe0f-107">[in] Um ponteiro para o novo cabeçalho CIL.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfe0f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dfe0f-108">Return Value</span></span>  
 <span data-ttu-id="dfe0f-109">Esse método retorna os HRESULTs específicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="dfe0f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfe0f-110">HRESULT</span></span>|<span data-ttu-id="dfe0f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfe0f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfe0f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfe0f-112">S_OK</span></span>|<span data-ttu-id="dfe0f-113">A substituição foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfe0f-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfe0f-114">Remarks</span></span>  
 <span data-ttu-id="dfe0f-115">Ao contrário do método [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) , o método `SetILFunctionBody` gerencia a memória necessária para o novo corpo cil.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="dfe0f-116">Isso significa que o corpo de CIL fornecido pelo criador de perfil não precisa ser alocado usando a interface [IMethodMalloc](imethodmalloc-interface.md) ou alocado em um intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="dfe0f-117">Ele pode ser alocado em qualquer heap.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-117">It can be allocated on any heap.</span></span> <span data-ttu-id="dfe0f-118">O criador de perfil pode liberar a memória usada para o corpo de CIL depois que `SetILFunctionBody` retorna.</span><span class="sxs-lookup"><span data-stu-id="dfe0f-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfe0f-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="dfe0f-119">Requirements</span></span>  
 <span data-ttu-id="dfe0f-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfe0f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfe0f-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dfe0f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dfe0f-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfe0f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfe0f-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfe0f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe0f-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="dfe0f-124">See also</span></span>

- [<span data-ttu-id="dfe0f-125">Interface ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="dfe0f-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
