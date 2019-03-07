---
title: Método ICorProfilerInfo4::GetReJITIDs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0361a4cd048f0b3be6bce47e52dd44ba3cea3475
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482750"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="aa18c-102">Método ICorProfilerInfo4::GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="aa18c-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="aa18c-103">Retorna uma matriz de IDs que identificam todos os recompilado por JIT versões da função especificada que ainda são alocadas.</span><span class="sxs-lookup"><span data-stu-id="aa18c-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="aa18c-104">Isso inclui versões recompilado por JIT funções que foram revertidas, posteriormente, mas ainda não liberadas (por exemplo, quando o domínio do aplicativo que contém a função revertida ainda está em uso).</span><span class="sxs-lookup"><span data-stu-id="aa18c-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa18c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa18c-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa18c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa18c-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="aa18c-107">[in] O `FunctionID` da instância de função para o qual será enumerada versões.</span><span class="sxs-lookup"><span data-stu-id="aa18c-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="aa18c-108">[in] O número de IDs recompilado por JIT alocados a `reJitIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="aa18c-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="aa18c-109">[out] O número real de IDs recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="aa18c-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="aa18c-110">[out] Uma matriz alocada pelo chamador que conterá as IDs recompilado por JIT para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="aa18c-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa18c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa18c-111">Remarks</span></span>  
 <span data-ttu-id="aa18c-112">`GetReJITIDs` Enumera as IDs de recompilado por JIT Active Directory para uma instância de função determinada.</span><span class="sxs-lookup"><span data-stu-id="aa18c-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="aa18c-113">Ele segue o mesmo padrão de uso como outro `ICorProfilerInfo` funções que aceitam buffers alocados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="aa18c-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa18c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa18c-114">Requirements</span></span>  
 <span data-ttu-id="aa18c-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa18c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa18c-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa18c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa18c-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa18c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa18c-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa18c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa18c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa18c-119">See also</span></span>
- [<span data-ttu-id="aa18c-120">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="aa18c-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="aa18c-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="aa18c-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="aa18c-122">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="aa18c-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
