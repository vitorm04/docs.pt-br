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
ms.openlocfilehash: e6c21e5ec9491e2ccade48a5019b284e333b5ead
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865929"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="ae597-102">Método ICorProfilerCallback::RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="ae597-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="ae597-103">Notifica o criador de perfil que o tempo de execução concluiu a suspensão de todos os threads de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae597-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae597-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae597-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae597-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae597-105">Remarks</span></span>  
 <span data-ttu-id="ae597-106">Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar em execução até tentarem inserir novamente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae597-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="ae597-107">Nesse ponto, eles também serão suspensos até que o tempo de execução seja retomado.</span><span class="sxs-lookup"><span data-stu-id="ae597-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="ae597-108">Isso também se aplica a novos threads que entram no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae597-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="ae597-109">Todos os threads no tempo de execução serão suspensos imediatamente se já estiverem no código passível de interrupção ou se forem solicitados a suspender quando acessarem o código passível de interrupção.</span><span class="sxs-lookup"><span data-stu-id="ae597-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="ae597-110">É garantido que o retorno de chamada de `RuntimeSuspendFinished` ocorrerá no mesmo thread que o retorno de chamada [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ae597-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae597-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ae597-111">Requirements</span></span>  
 <span data-ttu-id="ae597-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae597-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae597-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ae597-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae597-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae597-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae597-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae597-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae597-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="ae597-116">See also</span></span>

- [<span data-ttu-id="ae597-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ae597-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ae597-118">Método RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="ae597-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
