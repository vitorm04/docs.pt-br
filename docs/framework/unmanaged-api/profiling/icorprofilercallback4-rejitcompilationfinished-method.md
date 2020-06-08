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
ms.openlocfilehash: ff06c285bf5306977b520ed9ff845e70fb25989a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499370"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="c68f7-102">Método ICorProfilerCallback4::ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="c68f7-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="c68f7-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) concluiu a recompilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="c68f7-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c68f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c68f7-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c68f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c68f7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c68f7-106">no A ID da função que foi recompilada.</span><span class="sxs-lookup"><span data-stu-id="c68f7-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="c68f7-107">no A identidade da função de compilação JIT recompilada.</span><span class="sxs-lookup"><span data-stu-id="c68f7-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c68f7-108">no Um valor que indica se a recompilação JIT foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c68f7-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="c68f7-109">[in] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o thread de chamada retornar desse retorno de chamada; `false`para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c68f7-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="c68f7-110">Um valor de não `true` danifica o tempo de execução, mas pode afetar os resultados da criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="c68f7-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c68f7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c68f7-111">Requirements</span></span>  
 <span data-ttu-id="c68f7-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c68f7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c68f7-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c68f7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c68f7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c68f7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c68f7-115">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c68f7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68f7-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="c68f7-116">See also</span></span>

- [<span data-ttu-id="c68f7-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c68f7-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c68f7-118">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="c68f7-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="c68f7-119">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="c68f7-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="c68f7-120">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="c68f7-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
