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
ms.openlocfilehash: 52ab9a089b5def4f3db2f99abc5a718d66cca739
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863446"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="5e559-102">Método ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="5e559-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="5e559-103">Especifica a função implementada pelo criador de perfil que será chamada para mapear valores de `FunctionID` para valores alternativos, que são passados para os ganchos de entrada/saída da função do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="5e559-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e559-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e559-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e559-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e559-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="5e559-106">no Um ponteiro para a implementação de [FunctionIDMapper](functionidmapper-function.md) que será chamado para mapear os valores de `FunctionID` para seus valores alternativos.</span><span class="sxs-lookup"><span data-stu-id="5e559-106">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e559-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e559-107">Remarks</span></span>  
 <span data-ttu-id="5e559-108">As alternativas para os valores de `FunctionID` serão passadas para os ganchos de entrada/saída da função do criador de perfil ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)e [FunctionTailcall2](functiontailcall2-function.md)) que são especificados pelo método [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5e559-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="5e559-109">O `FunctionIDMapper` pode ser definido apenas uma vez e é recomendável defini-lo no retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5e559-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e559-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5e559-110">Requirements</span></span>  
 <span data-ttu-id="5e559-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e559-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e559-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5e559-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e559-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e559-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e559-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e559-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e559-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="5e559-115">See also</span></span>

- [<span data-ttu-id="5e559-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5e559-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
