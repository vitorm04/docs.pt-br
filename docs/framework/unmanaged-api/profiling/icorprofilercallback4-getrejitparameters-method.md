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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca176be93b92e44228d9b4063e87a62263e83e04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184867"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="8e9d5-102">Método ICorProfilerCallback4::GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="8e9d5-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="8e9d5-103">Permite que o criador de perfil de código definir sinalizadores de geração de código alternativo para um novo corpo de método recompilada.</span><span class="sxs-lookup"><span data-stu-id="8e9d5-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e9d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e9d5-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e9d5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e9d5-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="8e9d5-106">[in] O módulo que contém o método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="8e9d5-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="8e9d5-107">[in] O `MethodDef` do método para o qual o CLR precisa de parâmetros de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="8e9d5-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="8e9d5-108">[in] Um ponteiro para um [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface que o criador de perfil pode usar para fornecer informações de recompilação JIT para o método que está sendo recompilado.</span><span class="sxs-lookup"><span data-stu-id="8e9d5-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e9d5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e9d5-109">Remarks</span></span>  
 <span data-ttu-id="8e9d5-110">Os problemas CLR um `GetReJITParameters` retorno de chamada para que o criador de perfil pode especificar os parâmetros para recompilar um método em questão.</span><span class="sxs-lookup"><span data-stu-id="8e9d5-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="8e9d5-111">O `GetReJITParameters` retorno de chamada é emitido apenas uma vez por função; os parâmetros fornecidos pelo criador de perfil se aplicam a todas as instâncias dessa função.</span><span class="sxs-lookup"><span data-stu-id="8e9d5-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e9d5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e9d5-112">Requirements</span></span>  
 <span data-ttu-id="8e9d5-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e9d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e9d5-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e9d5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e9d5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e9d5-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8e9d5-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8e9d5-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e9d5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e9d5-117">See also</span></span>

- [<span data-ttu-id="8e9d5-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8e9d5-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8e9d5-119">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="8e9d5-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="8e9d5-120">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="8e9d5-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="8e9d5-121">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="8e9d5-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
