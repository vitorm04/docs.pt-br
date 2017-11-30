---
title: "Método ICorProfilerCallback::RuntimeSuspendFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c922ee4f986df22f213820b8aed60ea28a76377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="8ac22-102">Método ICorProfilerCallback::RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="8ac22-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="8ac22-103">Notifica o criador de perfil que o tempo de execução foi concluída a suspensão de todos os threads de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8ac22-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ac22-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8ac22-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ac22-105">Remarks</span></span>  
 <span data-ttu-id="8ac22-106">Todos os threads de tempo de execução que estão em código não gerenciado tem permissão para continuar a execução até que eles tentam inserir novamente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8ac22-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="8ac22-107">Nesse ponto que eles serão também suspensos até que o tempo de execução é retomada.</span><span class="sxs-lookup"><span data-stu-id="8ac22-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="8ac22-108">Isso também se aplica a novos segmentos que insira o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8ac22-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="8ac22-109">Todos os threads em tempo de execução são que seja suspenso imediatamente se eles já estão no código passível de interrupção ou são solicitadas quando atingem código passível de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8ac22-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="8ac22-110">O `RuntimeSuspendFinished` tem garantia de retorno de chamada ocorrer no mesmo thread, como o [Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8ac22-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac22-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ac22-111">Requirements</span></span>  
 <span data-ttu-id="8ac22-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ac22-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ac22-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ac22-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ac22-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ac22-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ac22-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ac22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac22-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ac22-116">See Also</span></span>  
 [<span data-ttu-id="8ac22-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8ac22-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8ac22-118">Método RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="8ac22-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
