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
ms.openlocfilehash: 805ceb60d2ac122df2382656b95b7bf5e7509bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855944"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="1a1dd-102">Método ICorProfilerInfo4::GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="1a1dd-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="1a1dd-103">Retorna uma matriz de IDs que identifica todas as versões recompiladas por JIT da função especificada que ainda estão alocadas.</span><span class="sxs-lookup"><span data-stu-id="1a1dd-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="1a1dd-104">Isso inclui versões recompiladas do JIT de funções que foram revertidas posteriormente, mas ainda não foram liberadas (por exemplo, quando o domínio do aplicativo que contém a função revertida ainda estiver em uso).</span><span class="sxs-lookup"><span data-stu-id="1a1dd-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1dd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a1dd-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a1dd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a1dd-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1a1dd-107">no O `FunctionID` da instância de função para a qual enumerar versões.</span><span class="sxs-lookup"><span data-stu-id="1a1dd-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="1a1dd-108">no O número de IDs recompiladas por JIT alocadas na `reJitIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="1a1dd-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="1a1dd-109">fora O número real de IDs recompiladas por JIT.</span><span class="sxs-lookup"><span data-stu-id="1a1dd-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="1a1dd-110">fora Uma matriz alocada pelo chamador que conterá as IDs de compilação JIT recompiladas para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="1a1dd-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a1dd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a1dd-111">Remarks</span></span>  
 <span data-ttu-id="1a1dd-112">`GetReJITIDs`enumera as IDs de recompilação JIT ativas para uma determinada instância de função.</span><span class="sxs-lookup"><span data-stu-id="1a1dd-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="1a1dd-113">Ele segue o mesmo padrão de uso que `ICorProfilerInfo` outras funções que aceitam buffers alocados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="1a1dd-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a1dd-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a1dd-114">Requirements</span></span>  
 <span data-ttu-id="1a1dd-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a1dd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a1dd-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1a1dd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1a1dd-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a1dd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a1dd-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a1dd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1dd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a1dd-119">See also</span></span>

- [<span data-ttu-id="1a1dd-120">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="1a1dd-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="1a1dd-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1a1dd-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1a1dd-122">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1a1dd-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
