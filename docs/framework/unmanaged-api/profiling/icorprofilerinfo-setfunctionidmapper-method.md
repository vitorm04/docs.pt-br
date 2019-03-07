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
ms.openlocfilehash: 52e8bc29ce03c54fd81ddc0d041cff6b9c35bb2d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475600"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="f3c28-102">Método ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="f3c28-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="f3c28-103">Especifica a função implementada pelo criador de perfil que será chamada para mapear `FunctionID` ganchos de entrada/saída de função de valores em valores alternativos que são passados para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f3c28-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3c28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3c28-104">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3c28-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3c28-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="f3c28-106">[in] Um ponteiro para o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementação que será chamada para mapear o `FunctionID` valores para seus valores alternativos.</span><span class="sxs-lookup"><span data-stu-id="f3c28-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3c28-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3c28-107">Remarks</span></span>  
 <span data-ttu-id="f3c28-108">As alternativas para o `FunctionID` valores serão passados para os ganchos de entrada/saída de função do criador de perfil ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) que são especificados pela [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f3c28-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="f3c28-109">O `FunctionIDMapper` pode ser definida apenas uma vez e é recomendável que você defina de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f3c28-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3c28-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3c28-110">Requirements</span></span>  
 <span data-ttu-id="f3c28-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3c28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3c28-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3c28-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3c28-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3c28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3c28-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3c28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c28-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3c28-115">See also</span></span>
- [<span data-ttu-id="f3c28-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f3c28-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
