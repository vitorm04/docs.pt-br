---
title: Método ICorProfilerInfo3::EnumJITedFunctions
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b05ad4bddc6d82c486d0b460cd946df8299bf3e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466317"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="b2cf5-102">Método ICorProfilerInfo3::EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="b2cf5-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="b2cf5-103">Retorna um enumerador para todas as funções que foram previamente compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="b2cf5-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2cf5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2cf5-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2cf5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2cf5-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="b2cf5-106">[out] Um ponteiro para o [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerador.</span><span class="sxs-lookup"><span data-stu-id="b2cf5-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2cf5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2cf5-107">Remarks</span></span>  
 <span data-ttu-id="b2cf5-108">Esse método pode se sobrepor `JITCompilation` retornos de chamada, como o [ICorProfilerCallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b2cf5-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="b2cf5-109">O enumerador retornado por esse método não inclui funções que são carregadas de imagens nativas geradas com Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="b2cf5-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2cf5-110">Enumeração retornada inclui apenas "0" para o valor da `COR_PRF_FUNCTION::reJitId` campo.</span><span class="sxs-lookup"><span data-stu-id="b2cf5-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="b2cf5-111">Se você precisar válida `COR_PRF_FUNCTION::reJitId` valores, use o [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b2cf5-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2cf5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2cf5-112">Requirements</span></span>  
 <span data-ttu-id="b2cf5-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2cf5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2cf5-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2cf5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2cf5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2cf5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2cf5-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2cf5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2cf5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2cf5-117">See also</span></span>
- [<span data-ttu-id="b2cf5-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="b2cf5-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b2cf5-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b2cf5-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b2cf5-120">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b2cf5-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
