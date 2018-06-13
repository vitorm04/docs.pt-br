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
ms.openlocfilehash: dbf447e1325b4acaa26c9bb16d7d1a736eb20a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453545"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="bb246-102">Método ICorProfilerCallback::JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="bb246-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="bb246-103">Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a compilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="bb246-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb246-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb246-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb246-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb246-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="bb246-106">[in] A ID da função que foi compilada.</span><span class="sxs-lookup"><span data-stu-id="bb246-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="bb246-107">[in] Um valor que indica se a compilação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bb246-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="bb246-108">[in] Um valor que indica o criador de perfil se bloqueio afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bb246-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="bb246-109">O valor é `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="bb246-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="bb246-110">Embora um valor de `true` não prejudicarão o tempo de execução, ele pode afetar os resultados da criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="bb246-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb246-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb246-111">Requirements</span></span>  
 <span data-ttu-id="bb246-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb246-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb246-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb246-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb246-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb246-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb246-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb246-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb246-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb246-116">See Also</span></span>  
 [<span data-ttu-id="bb246-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bb246-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="bb246-118">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="bb246-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
