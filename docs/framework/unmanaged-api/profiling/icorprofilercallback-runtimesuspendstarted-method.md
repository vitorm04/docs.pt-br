---
title: "Método ICorProfilerCallback::RuntimeSuspendStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 358536aa51dfef2d079813b34eddbd1b01294bcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="016c5-102">Método ICorProfilerCallback::RuntimeSuspendStarted</span><span class="sxs-lookup"><span data-stu-id="016c5-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="016c5-103">Notifica o criador de perfil que o tempo de execução está prestes a suspender todos os threads de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="016c5-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="016c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="016c5-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="016c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="016c5-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="016c5-106">[in] Um valor de [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeração que indica o motivo para a suspensão.</span><span class="sxs-lookup"><span data-stu-id="016c5-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="016c5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="016c5-107">Remarks</span></span>  
 <span data-ttu-id="016c5-108">Todos os threads de tempo de execução que estão em código não gerenciado tem permissão para continuar a execução até que eles tentam inserir novamente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="016c5-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="016c5-109">Nesse ponto que eles serão também suspensos até que o tempo de execução é retomada.</span><span class="sxs-lookup"><span data-stu-id="016c5-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="016c5-110">Isso também se aplica a novos segmentos que insira o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="016c5-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="016c5-111">Todos os threads em tempo de execução são que seja suspenso imediatamente se eles já estão no código passível de interrupção ou são solicitadas quando atingem código passível de suspensão.</span><span class="sxs-lookup"><span data-stu-id="016c5-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="016c5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="016c5-112">Requirements</span></span>  
 <span data-ttu-id="016c5-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="016c5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="016c5-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="016c5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="016c5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="016c5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="016c5-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="016c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="016c5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="016c5-117">See Also</span></span>  
 [<span data-ttu-id="016c5-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="016c5-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="016c5-119">Método RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="016c5-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)  
 [<span data-ttu-id="016c5-120">Método RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="016c5-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
