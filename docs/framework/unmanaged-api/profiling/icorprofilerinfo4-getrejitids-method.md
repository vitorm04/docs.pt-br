---
title: "Método ICorProfilerInfo4::GetReJITIDs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetReJITIDs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc16cd932fc2ce0cf5cb53c227081501e79ed2d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="cab2a-102">Método ICorProfilerInfo4::GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="cab2a-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="cab2a-103">Retorna uma matriz de IDs de identificar todos os recompilado JIT versões da função especificada ainda alocados.</span><span class="sxs-lookup"><span data-stu-id="cab2a-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="cab2a-104">Isso inclui versões recompilado JIT de funções que foram posteriormente revertidas, mas ainda não liberadas (por exemplo, quando o domínio de aplicativo que contém a função revertida ainda está em uso).</span><span class="sxs-lookup"><span data-stu-id="cab2a-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab2a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cab2a-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cab2a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cab2a-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cab2a-107">[in] O `FunctionID` da instância de função para o qual enumerar versões.</span><span class="sxs-lookup"><span data-stu-id="cab2a-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="cab2a-108">[in] O número de IDs recompilado JIT alocados a `reJitIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="cab2a-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="cab2a-109">[out] O número real de IDs de recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="cab2a-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="cab2a-110">[out] Uma matriz alocada pelo chamador que conterá as IDs recompilado JIT para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="cab2a-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cab2a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cab2a-111">Remarks</span></span>  
 <span data-ttu-id="cab2a-112">`GetReJITIDs`Enumera as IDs de recompilado JIT ativas para uma instância de função determinada.</span><span class="sxs-lookup"><span data-stu-id="cab2a-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="cab2a-113">Ele segue o mesmo padrão de uso como outros `ICorProfilerInfo` funções que aceitam buffers alocada pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="cab2a-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cab2a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cab2a-114">Requirements</span></span>  
 <span data-ttu-id="cab2a-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cab2a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cab2a-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cab2a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cab2a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cab2a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cab2a-118">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab2a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cab2a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cab2a-119">See Also</span></span>  
 [<span data-ttu-id="cab2a-120">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="cab2a-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="cab2a-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="cab2a-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="cab2a-122">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="cab2a-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
