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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5556fecb6251a2dd6a131332dbff1b5ca2f5d95
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493330"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="d5e80-102">Método ICorProfilerCallback::JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="d5e80-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="d5e80-103">Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a compilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="d5e80-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5e80-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5e80-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d5e80-106">[in] A ID da função que foi compilada.</span><span class="sxs-lookup"><span data-stu-id="d5e80-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d5e80-107">[in] Um valor que indica se a compilação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d5e80-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="d5e80-108">[in] Um valor que indica o criador de perfil, se o bloqueio afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d5e80-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="d5e80-109">O valor será `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="d5e80-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="d5e80-110">Embora um valor de `true` não danificará o tempo de execução, ele pode afetar os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="d5e80-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e80-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5e80-111">Requirements</span></span>  
 <span data-ttu-id="d5e80-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e80-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e80-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5e80-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5e80-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5e80-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5e80-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e80-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e80-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5e80-116">See also</span></span>
- [<span data-ttu-id="d5e80-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d5e80-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d5e80-118">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="d5e80-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
