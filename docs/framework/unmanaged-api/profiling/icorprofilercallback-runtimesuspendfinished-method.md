---
title: Método ICorProfilerCallback::RuntimeSuspendFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f69c39938384c7feca28ae40aba3e80a0ba28ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706648"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="8e24b-102">Método ICorProfilerCallback::RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="8e24b-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="8e24b-103">Notifica o criador de perfil que o tempo de execução foi concluída a suspensão de todos os segmentos de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e24b-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e24b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e24b-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8e24b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e24b-105">Remarks</span></span>  
 <span data-ttu-id="8e24b-106">Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar a execução até que eles tentarem inserir novamente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e24b-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="8e24b-107">Nesse ponto que eles serão também suspensos até que o tempo de execução é retomada.</span><span class="sxs-lookup"><span data-stu-id="8e24b-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="8e24b-108">Isso também se aplica a novos threads que insira o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e24b-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="8e24b-109">Todos os threads no tempo de execução são que seja suspenso imediatamente se eles já estão no código passível de interrupção, ou eles são solicitados a suspender quando atingem código passível de interrupção.</span><span class="sxs-lookup"><span data-stu-id="8e24b-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="8e24b-110">O `RuntimeSuspendFinished` retorno de chamada é garantido que ocorrem no mesmo thread que o [ICorProfilerCallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8e24b-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e24b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e24b-111">Requirements</span></span>  
 <span data-ttu-id="8e24b-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e24b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e24b-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e24b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e24b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e24b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e24b-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e24b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e24b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e24b-116">See also</span></span>
- [<span data-ttu-id="8e24b-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8e24b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8e24b-118">Método RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="8e24b-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
