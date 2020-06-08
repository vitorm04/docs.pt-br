---
title: Método ICorProfilerCallback::JITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 0da67f0d4be779cc21481d03a21209620289888e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500047"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="e73bd-102">Método ICorProfilerCallback::JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="e73bd-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="e73bd-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) concluiu a compilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="e73bd-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e73bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e73bd-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e73bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e73bd-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="e73bd-106">\[in] a ID da função que foi compilada.</span><span class="sxs-lookup"><span data-stu-id="e73bd-106">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="e73bd-107">\[in] um valor que indica se A compilação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e73bd-107">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="e73bd-108">\[in] um valor que indica ao criador de perfil se o bloqueio afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e73bd-108">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="e73bd-109">O valor é `true` se o bloqueio pode fazer com que o tempo de execução aguarde o thread de chamada retornar desse retorno de chamada; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="e73bd-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="e73bd-110">Embora um valor de `true` não danifique o tempo de execução, ele pode distorcer os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="e73bd-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="e73bd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e73bd-111">Requirements</span></span>  
 <span data-ttu-id="e73bd-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e73bd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e73bd-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e73bd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e73bd-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e73bd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e73bd-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e73bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73bd-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e73bd-116">See also</span></span>

- [<span data-ttu-id="e73bd-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e73bd-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e73bd-118">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="e73bd-118">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
