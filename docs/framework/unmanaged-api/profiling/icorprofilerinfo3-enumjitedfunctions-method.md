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
ms.openlocfilehash: d21a793a88cd7561da9acb7daab2dc3bfecf0fc7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449766"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="00184-102">Método ICorProfilerInfo3::EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="00184-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="00184-103">Retorna um enumerador para todas as funções que foram compiladas por JIT anteriormente.</span><span class="sxs-lookup"><span data-stu-id="00184-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00184-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00184-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00184-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00184-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="00184-106">fora Um ponteiro para o enumerador [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="00184-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00184-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="00184-107">Remarks</span></span>  
 <span data-ttu-id="00184-108">Esse método pode se sobrepor com `JITCompilation` retornos de chamada como o método [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00184-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="00184-109">O enumerador retornado por esse método não inclui funções que são carregadas de imagens nativas geradas com NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="00184-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00184-110">A enumeração retornada inclui apenas "0" para o valor do campo `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="00184-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="00184-111">Se você precisar de valores de `COR_PRF_FUNCTION::reJitId` válidos, use o método [ICorProfilerInfo4:: EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00184-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00184-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00184-112">Requirements</span></span>  
 <span data-ttu-id="00184-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00184-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00184-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00184-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00184-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00184-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00184-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00184-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00184-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00184-117">See also</span></span>

- [<span data-ttu-id="00184-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="00184-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="00184-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="00184-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="00184-120">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="00184-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
