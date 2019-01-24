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
ms.openlocfilehash: 4d2e75d357b1f56df676163744015a1a3f77c17b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530743"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="0b5e9-102">Método ICorProfilerCallback::JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="0b5e9-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="0b5e9-103">Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a compilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b5e9-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b5e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b5e9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0b5e9-106">[in] A ID da função que foi compilada.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="0b5e9-107">[in] Um valor que indica se a compilação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="0b5e9-108">[in] Um valor que indica o criador de perfil, se o bloqueio afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="0b5e9-109">O valor será `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="0b5e9-110">Embora um valor de `true` não danificará o tempo de execução, ele pode afetar os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5e9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b5e9-111">Requirements</span></span>  
 <span data-ttu-id="0b5e9-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5e9-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0b5e9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b5e9-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b5e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b5e9-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b5e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5e9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b5e9-116">See also</span></span>
- [<span data-ttu-id="0b5e9-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0b5e9-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="0b5e9-118">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="0b5e9-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
