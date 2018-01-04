---
title: "Método ICorProfilerInfo3::EnumJITedFunctions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumJITedFunctions Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11a6b34be4f9bf046749941ac12895bf7040e331
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="c42f2-102">Método ICorProfilerInfo3::EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="c42f2-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="c42f2-103">Retorna um enumerador para todas as funções que foram anteriormente compilados JIT.</span><span class="sxs-lookup"><span data-stu-id="c42f2-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c42f2-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c42f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c42f2-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c42f2-106">[out] Um ponteiro para o [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerador.</span><span class="sxs-lookup"><span data-stu-id="c42f2-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c42f2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c42f2-107">Remarks</span></span>  
 <span data-ttu-id="c42f2-108">Esse método pode sobrepor `JITCompilation` retornos de chamada, como o [: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c42f2-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="c42f2-109">O enumerador retornado por esse método não inclui funções que são carregadas de imagens nativas geradas com Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="c42f2-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c42f2-110">A enumeração retornada inclui apenas "0" para o valor da `COR_PRF_FUNCTION::reJitId` campo.</span><span class="sxs-lookup"><span data-stu-id="c42f2-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="c42f2-111">Se você precisar válido `COR_PRF_FUNCTION::reJitId` valores, use o [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c42f2-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c42f2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c42f2-112">Requirements</span></span>  
 <span data-ttu-id="c42f2-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c42f2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c42f2-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c42f2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c42f2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c42f2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c42f2-116">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c42f2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42f2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c42f2-117">See Also</span></span>  
 [<span data-ttu-id="c42f2-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="c42f2-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="c42f2-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c42f2-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c42f2-120">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c42f2-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
