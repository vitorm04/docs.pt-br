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
ms.openlocfilehash: 527e48d02d5267d6ae41214686c2e8c997d85dca
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499539"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="7bb3c-102">Método ICorProfilerCallback4::GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="7bb3c-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="7bb3c-103">Permite que o criador de perfil de código defina sinalizadores de geração de código alternativos para um novo corpo de método recompilado.</span><span class="sxs-lookup"><span data-stu-id="7bb3c-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bb3c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb3c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bb3c-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="7bb3c-106">no O módulo que contém o método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="7bb3c-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="7bb3c-107">no O `MethodDef` do método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="7bb3c-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="7bb3c-108">no Um ponteiro para uma interface [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) que o criador de perfil pode usar para fornecer informações de recompilação JIT para o método que está sendo recompilado.</span><span class="sxs-lookup"><span data-stu-id="7bb3c-108">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bb3c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bb3c-109">Remarks</span></span>  
 <span data-ttu-id="7bb3c-110">O CLR emite um `GetReJITParameters` retorno de chamada para que o criador de perfil possa especificar os parâmetros para a recompilação de um determinado método.</span><span class="sxs-lookup"><span data-stu-id="7bb3c-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="7bb3c-111">O `GetReJITParameters` retorno de chamada é emitido apenas uma vez por função; os parâmetros fornecidos pelo criador de perfil se aplicam a todas as instâncias dessa função.</span><span class="sxs-lookup"><span data-stu-id="7bb3c-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb3c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bb3c-112">Requirements</span></span>  
 <span data-ttu-id="7bb3c-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb3c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb3c-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7bb3c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bb3c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bb3c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bb3c-116">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb3c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb3c-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="7bb3c-117">See also</span></span>

- [<span data-ttu-id="7bb3c-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7bb3c-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="7bb3c-119">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="7bb3c-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="7bb3c-120">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="7bb3c-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="7bb3c-121">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="7bb3c-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
