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
ms.openlocfilehash: 9069498a4f62f4d9dbb50a7075323b14c3cc5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868441"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="3d92a-102">Método ICorProfilerInfo4::GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="3d92a-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="3d92a-103">Retorna uma matriz de IDs que identifica todas as versões recompiladas por JIT da função especificada que ainda estão alocadas.</span><span class="sxs-lookup"><span data-stu-id="3d92a-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="3d92a-104">Isso inclui versões recompiladas do JIT de funções que foram revertidas posteriormente, mas ainda não foram liberadas (por exemplo, quando o domínio do aplicativo que contém a função revertida ainda estiver em uso).</span><span class="sxs-lookup"><span data-stu-id="3d92a-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d92a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d92a-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d92a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d92a-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3d92a-107">no O `FunctionID` da instância de função para a qual enumerar versões.</span><span class="sxs-lookup"><span data-stu-id="3d92a-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="3d92a-108">no O número de IDs recompiladas por JIT alocadas na matriz de `reJitIds`.</span><span class="sxs-lookup"><span data-stu-id="3d92a-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="3d92a-109">fora O número real de IDs recompiladas por JIT.</span><span class="sxs-lookup"><span data-stu-id="3d92a-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="3d92a-110">fora Uma matriz alocada pelo chamador que conterá as IDs de compilação JIT recompiladas para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="3d92a-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d92a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d92a-111">Remarks</span></span>  
 <span data-ttu-id="3d92a-112">`GetReJITIDs` enumera as IDs de recompilação de JIT ativas para uma determinada instância de função.</span><span class="sxs-lookup"><span data-stu-id="3d92a-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="3d92a-113">Ele segue o mesmo padrão de uso que outras funções `ICorProfilerInfo` que aceitam buffers alocados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="3d92a-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d92a-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="3d92a-114">Requirements</span></span>  
 <span data-ttu-id="3d92a-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d92a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d92a-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3d92a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d92a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d92a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d92a-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d92a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d92a-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="3d92a-119">See also</span></span>

- [<span data-ttu-id="3d92a-120">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="3d92a-120">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="3d92a-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3d92a-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3d92a-122">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3d92a-122">Profiling</span></span>](index.md)
