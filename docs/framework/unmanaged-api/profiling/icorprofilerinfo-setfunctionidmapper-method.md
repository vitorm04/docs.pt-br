---
title: Método ICorProfilerInfo::SetFunctionIDMapper
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e5d9c9596d0bb5e61bd7aed4caaa986759cfa54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="341bc-102">Método ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="341bc-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="341bc-103">Especifica a função implementado pelo gerador de perfil que será chamada para mapear `FunctionID` valores para valores alternativos, que são passados para o criador de perfil de função ganchos de entrada/saída.</span><span class="sxs-lookup"><span data-stu-id="341bc-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="341bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="341bc-104">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="341bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="341bc-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="341bc-106">[in] Um ponteiro para o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementação que será chamada para mapear o `FunctionID` valores para seus valores alternativos.</span><span class="sxs-lookup"><span data-stu-id="341bc-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="341bc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="341bc-107">Remarks</span></span>  
 <span data-ttu-id="341bc-108">As alternativas para o `FunctionID` valores serão passados para conexões de entrada/saída de função do criador de perfil ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) que são especificadas pelo [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="341bc-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="341bc-109">O `FunctionIDMapper` pode ser definido apenas uma vez e é recomendável que você defina no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="341bc-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="341bc-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="341bc-110">Requirements</span></span>  
 <span data-ttu-id="341bc-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="341bc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="341bc-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="341bc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="341bc-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="341bc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="341bc-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="341bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341bc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="341bc-115">See Also</span></span>  
 [<span data-ttu-id="341bc-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="341bc-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
