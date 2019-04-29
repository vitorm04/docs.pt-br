---
title: Método ICorProfilerCallback4::ReJITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ec2981cbee4675f9cd2a4fd13d507f50ad2a3ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597135"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="9be20-102">Método ICorProfilerCallback4::ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="9be20-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="9be20-103">Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a recompilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="9be20-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be20-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9be20-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9be20-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9be20-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9be20-106">[in] A ID da função recompilada.</span><span class="sxs-lookup"><span data-stu-id="9be20-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="9be20-107">[in] A identidade da função recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="9be20-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="9be20-108">[in] Um valor que indica se a recompilação JIT foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9be20-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="9be20-109">[in] `true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9be20-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="9be20-110">Um valor de `true` não prejudicará o tempo de execução, mas podem afetar os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="9be20-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9be20-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9be20-111">Requirements</span></span>  
 <span data-ttu-id="9be20-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9be20-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be20-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9be20-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9be20-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9be20-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9be20-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9be20-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be20-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9be20-116">See also</span></span>

- [<span data-ttu-id="9be20-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9be20-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9be20-118">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="9be20-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="9be20-119">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="9be20-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="9be20-120">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="9be20-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
