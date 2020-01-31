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
ms.openlocfilehash: f1cfef464569b577923fbb16624c99358998d29c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866241"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="370ba-102">Método ICorProfilerCallback::JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="370ba-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="370ba-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) concluiu a compilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="370ba-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="370ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="370ba-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="370ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="370ba-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="370ba-106">\[em] a ID da função que foi compilada.</span><span class="sxs-lookup"><span data-stu-id="370ba-106">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="370ba-107">\[em] um valor que indica se a compilação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="370ba-107">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="370ba-108">\[em] um valor que indica ao criador de perfil se o bloqueio afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="370ba-108">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="370ba-109">O valor será `true` se o bloqueio puder fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="370ba-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="370ba-110">Embora um valor de `true` não danifique o tempo de execução, ele pode distorcer os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="370ba-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="370ba-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="370ba-111">Requirements</span></span>  
 <span data-ttu-id="370ba-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="370ba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="370ba-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="370ba-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="370ba-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="370ba-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="370ba-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="370ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="370ba-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="370ba-116">See also</span></span>

- [<span data-ttu-id="370ba-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="370ba-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="370ba-118">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="370ba-118">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
