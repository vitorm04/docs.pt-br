---
title: "Método ICorProfilerCallback4::GetReJITParameters"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.GetReJITParameters
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03e5440fbd016f52642a5626b0cf0b82e7ecea45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="a132a-102">Método ICorProfilerCallback4::GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="a132a-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="a132a-103">Permite que o criador de perfil de código definir sinalizadores de geração de código alternativo para um novo corpo de método recompilada.</span><span class="sxs-lookup"><span data-stu-id="a132a-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a132a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a132a-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a132a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a132a-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a132a-106">[in] O módulo que contém o método para o qual o CLR precisa de parâmetros de recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="a132a-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="a132a-107">[in] O `MethodDef` do método para os quais o CLR precisa de parâmetros de recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="a132a-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="a132a-108">[in] Um ponteiro para um [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface que pode usar o criador de perfil para fornecer informações de recompilação de JIT para o método sendo recompilado.</span><span class="sxs-lookup"><span data-stu-id="a132a-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a132a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a132a-109">Remarks</span></span>  
 <span data-ttu-id="a132a-110">Os problemas CLR um `GetReJITParameters` retorno de chamada para que o criador de perfil pode especificar os parâmetros para recompilar um determinado método.</span><span class="sxs-lookup"><span data-stu-id="a132a-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="a132a-111">O `GetReJITParameters` retorno de chamada é emitido somente uma vez por função; os parâmetros fornecidos pelo criador de perfil se aplicam a todas as instâncias dessa função.</span><span class="sxs-lookup"><span data-stu-id="a132a-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a132a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a132a-112">Requirements</span></span>  
 <span data-ttu-id="a132a-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a132a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a132a-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a132a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a132a-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a132a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a132a-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a132a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a132a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a132a-117">See Also</span></span>  
 [<span data-ttu-id="a132a-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a132a-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a132a-119">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="a132a-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="a132a-120">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="a132a-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="a132a-121">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="a132a-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
