---
title: Método ICorProfilerInfo3::SetFunctionIDMapper2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c3046b78aeaee2d9a6264cc68fc61d1fe02cbb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626505"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="d5928-102">Método ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d5928-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="d5928-103">Especifica a função implementada pelo criador de perfil que será chamada para mapear `FunctionID` ganchos de entrada/saída de função de valores em valores alternativos que são passados para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="d5928-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="d5928-104">Este método estende o [ICorProfilerInfo:: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) método com um parâmetro de dados adicionais que os criadores de perfis podem usar para resolver a ambiguidade os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="d5928-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5928-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5928-105">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5928-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5928-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="d5928-107">[in] Um ponteiro para um [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementação que será chamada para mapear o `FunctionID` valores para seus valores alternativos.</span><span class="sxs-lookup"><span data-stu-id="d5928-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="d5928-108">[in] Um ponteiro que é passado a cada [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) feita pelo tempo de execução atual de chamada de função.</span><span class="sxs-lookup"><span data-stu-id="d5928-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="d5928-109">O criador de perfil pode usar essas informações para resolver a ambiguidade os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="d5928-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5928-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5928-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5928-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5928-111">Remarks</span></span>  
 <span data-ttu-id="d5928-112">As alternativas para os valores de FunctionID serão passadas para os ganchos de entrada/saída de função do criador de perfil ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; ou [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) que são especificados pela [ SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) ou [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="d5928-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="d5928-113">O `FunctionIDMapper2` método pode ser definido apenas uma vez; é recomendável que você defina de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d5928-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5928-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5928-114">Requirements</span></span>  
 <span data-ttu-id="d5928-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5928-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5928-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5928-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5928-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5928-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5928-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5928-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5928-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5928-119">See also</span></span>
- [<span data-ttu-id="d5928-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d5928-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d5928-121">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="d5928-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d5928-122">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d5928-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d5928-123">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d5928-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
