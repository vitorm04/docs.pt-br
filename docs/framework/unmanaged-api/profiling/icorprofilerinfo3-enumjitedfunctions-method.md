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
ms.openlocfilehash: 5ceb1d22500f73a29ffdfa6f16907478628358c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969390"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="3ea8c-102">Método ICorProfilerInfo3::EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="3ea8c-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="3ea8c-103">Retorna um enumerador para todas as funções que foram compiladas por JIT anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3ea8c-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea8c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ea8c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ea8c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ea8c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3ea8c-106">fora Um ponteiro para o enumerador [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3ea8c-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ea8c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ea8c-107">Remarks</span></span>  
 <span data-ttu-id="3ea8c-108">Esse método pode se sobrepor `JITCompilation` a retornos de chamada como o método [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3ea8c-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="3ea8c-109">O enumerador retornado por esse método não inclui funções que são carregadas de imagens nativas geradas com NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="3ea8c-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ea8c-110">A enumeração retornada inclui apenas "0" para o valor do `COR_PRF_FUNCTION::reJitId` campo.</span><span class="sxs-lookup"><span data-stu-id="3ea8c-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="3ea8c-111">Se você precisar de `COR_PRF_FUNCTION::reJitId` valores válidos, use o método [ICorProfilerInfo4:: EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3ea8c-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea8c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ea8c-112">Requirements</span></span>  
 <span data-ttu-id="3ea8c-113">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea8c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea8c-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ea8c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ea8c-115">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ea8c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ea8c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea8c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea8c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ea8c-117">See also</span></span>

- [<span data-ttu-id="3ea8c-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="3ea8c-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3ea8c-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3ea8c-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="3ea8c-120">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3ea8c-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
