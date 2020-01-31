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
ms.openlocfilehash: 858d65783515a89a434cf719ef9d5a999643094c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865305"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="326d5-102">Método ICorProfilerCallback4::GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="326d5-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="326d5-103">Permite que o criador de perfil de código defina sinalizadores de geração de código alternativos para um novo corpo de método recompilado.</span><span class="sxs-lookup"><span data-stu-id="326d5-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="326d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="326d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="326d5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="326d5-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="326d5-106">no O módulo que contém o método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="326d5-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="326d5-107">no O `MethodDef` do método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="326d5-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="326d5-108">no Um ponteiro para uma interface [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) que o criador de perfil pode usar para fornecer informações de recompilação JIT para o método que está sendo recompilado.</span><span class="sxs-lookup"><span data-stu-id="326d5-108">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="326d5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="326d5-109">Remarks</span></span>  
 <span data-ttu-id="326d5-110">O CLR emite um retorno de chamada `GetReJITParameters` para que o criador de perfil possa especificar os parâmetros para a recompilação de um determinado método.</span><span class="sxs-lookup"><span data-stu-id="326d5-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="326d5-111">O retorno de chamada `GetReJITParameters` é emitido apenas uma vez por função; os parâmetros fornecidos pelo criador de perfil se aplicam a todas as instâncias dessa função.</span><span class="sxs-lookup"><span data-stu-id="326d5-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="326d5-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="326d5-112">Requirements</span></span>  
 <span data-ttu-id="326d5-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="326d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="326d5-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="326d5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="326d5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="326d5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="326d5-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="326d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326d5-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="326d5-117">See also</span></span>

- [<span data-ttu-id="326d5-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="326d5-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="326d5-119">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="326d5-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="326d5-120">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="326d5-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="326d5-121">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="326d5-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
