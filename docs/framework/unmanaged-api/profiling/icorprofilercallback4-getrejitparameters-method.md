---
title: Método ICorProfilerCallback4::GetReJITParameters
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: d81d7275d197de1dfc99b135377459f509c2651f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439443"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="32707-102">Método ICorProfilerCallback4::GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="32707-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="32707-103">Permite que o criador de perfil de código defina sinalizadores de geração de código alternativos para um novo corpo de método recompilado.</span><span class="sxs-lookup"><span data-stu-id="32707-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32707-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32707-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32707-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32707-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="32707-106">no O módulo que contém o método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="32707-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="32707-107">no O `MethodDef` do método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="32707-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="32707-108">no Um ponteiro para uma interface [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) que o criador de perfil pode usar para fornecer informações de recompilação JIT para o método que está sendo recompilado.</span><span class="sxs-lookup"><span data-stu-id="32707-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32707-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="32707-109">Remarks</span></span>  
 <span data-ttu-id="32707-110">O CLR emite um retorno de chamada `GetReJITParameters` para que o criador de perfil possa especificar os parâmetros para a recompilação de um determinado método.</span><span class="sxs-lookup"><span data-stu-id="32707-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="32707-111">O retorno de chamada `GetReJITParameters` é emitido apenas uma vez por função; os parâmetros fornecidos pelo criador de perfil se aplicam a todas as instâncias dessa função.</span><span class="sxs-lookup"><span data-stu-id="32707-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32707-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32707-112">Requirements</span></span>  
 <span data-ttu-id="32707-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32707-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32707-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="32707-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32707-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32707-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32707-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32707-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32707-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32707-117">See also</span></span>

- [<span data-ttu-id="32707-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="32707-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="32707-119">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="32707-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="32707-120">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="32707-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="32707-121">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="32707-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
