---
title: "Método ICorProfilerInfo2::GetBoxClassLayout"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ef6df997a4ba4369b87789e47ac7ead2206162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="c3d47-102">Método ICorProfilerInfo2::GetBoxClassLayout</span><span class="sxs-lookup"><span data-stu-id="c3d47-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="c3d47-103">Obtém informações sobre onde o tipo de valor especificado está localizado ao é demarcado.</span><span class="sxs-lookup"><span data-stu-id="c3d47-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d47-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3d47-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3d47-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3d47-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="c3d47-106">[in] A ID da classe que descreve o tipo de valor é demarcado.</span><span class="sxs-lookup"><span data-stu-id="c3d47-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="c3d47-107">[out] Um inteiro que é o deslocamento, em relação o ponteiro de ID de objeto box, do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="c3d47-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3d47-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3d47-108">Remarks</span></span>  
 <span data-ttu-id="c3d47-109">O `pBufferOffset` valor é o local do tipo de valor em uma caixa.</span><span class="sxs-lookup"><span data-stu-id="c3d47-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="c3d47-110">Depois de `pBufferOffset` é aplicado a um objeto box, layout de classe do tipo de valor pode ser usado para interpretar o valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="c3d47-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d47-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3d47-111">Requirements</span></span>  
 <span data-ttu-id="c3d47-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d47-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d47-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3d47-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3d47-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3d47-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3d47-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d47-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d47-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3d47-116">See Also</span></span>  
 [<span data-ttu-id="c3d47-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c3d47-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c3d47-118">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="c3d47-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
