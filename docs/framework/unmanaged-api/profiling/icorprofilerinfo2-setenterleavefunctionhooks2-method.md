---
title: Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f95a404ce7124a76ee527cdc70ccccf103838b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076790"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="ad81b-102">Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="ad81b-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="ad81b-103">Especifica as funções implementada pelo criador de perfil a ser chamada nas versões atualizadas do "enter", "Sair" e "chamada tail" ganchos de funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="ad81b-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad81b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad81b-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad81b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad81b-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="ad81b-106">[in] Um ponteiro para a implementação a ser usado como o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ad81b-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="ad81b-107">[in] Um ponteiro para a implementação a ser usado como o [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ad81b-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="ad81b-108">[in] Um ponteiro para a implementação a ser usado como o [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ad81b-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad81b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad81b-109">Remarks</span></span>  
 <span data-ttu-id="ad81b-110">O `SetEnterLeaveFunctionHooks2` método é semelhante de [ICorProfilerInfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ad81b-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="ad81b-111">Use a primeira opção para especificar funções a serem usadas como as versões mais recentes de enter/deixar/tailcall retornos de chamada e o segundo para especificar as funções a serem usadas como as versões mais antigas dos retornos de chamada enter/deixar/chamada tail.</span><span class="sxs-lookup"><span data-stu-id="ad81b-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="ad81b-112">Apenas um conjunto de retornos de chamada pode estar ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="ad81b-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="ad81b-113">Portanto, se um criador de perfil chama ambos `ICorProfilerInfo::SetEnterLeaveFunctionHooks` e `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` é usado.</span><span class="sxs-lookup"><span data-stu-id="ad81b-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="ad81b-114">O `SetEnterLeaveFunctionHooks2` método pode ser chamado apenas do criador de perfil [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ad81b-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad81b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad81b-115">Requirements</span></span>  
 <span data-ttu-id="ad81b-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad81b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad81b-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad81b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad81b-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad81b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad81b-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad81b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad81b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad81b-120">See also</span></span>

- [<span data-ttu-id="ad81b-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="ad81b-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="ad81b-122">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="ad81b-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
