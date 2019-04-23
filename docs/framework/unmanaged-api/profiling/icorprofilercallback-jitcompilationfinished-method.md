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
ms.openlocfilehash: 1abc4dd209581c9f7c8e950ea1addc74c611d248
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226052"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="a95d1-102">Método ICorProfilerCallback::JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="a95d1-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="a95d1-103">Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a compilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="a95d1-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a95d1-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a95d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a95d1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a95d1-106">[in] A ID da função que foi compilada.</span><span class="sxs-lookup"><span data-stu-id="a95d1-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="a95d1-107">[in] Um valor que indica se a compilação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a95d1-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="a95d1-108">[in] Um valor que indica o criador de perfil, se o bloqueio afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a95d1-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="a95d1-109">O valor será `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a95d1-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="a95d1-110">Embora um valor de `true` não danificará o tempo de execução, ele pode afetar os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="a95d1-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a95d1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a95d1-111">Requirements</span></span>  
 <span data-ttu-id="a95d1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a95d1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a95d1-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a95d1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a95d1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a95d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a95d1-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a95d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95d1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a95d1-116">See also</span></span>

- [<span data-ttu-id="a95d1-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a95d1-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a95d1-118">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="a95d1-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
