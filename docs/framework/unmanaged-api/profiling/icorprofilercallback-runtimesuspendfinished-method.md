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
ms.openlocfilehash: 64611fa7368f05de906b71b08bda8f1e7c460bf3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503231"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="251d1-102">Método ICorProfilerCallback::RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="251d1-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="251d1-103">Notifica o criador de perfil que o tempo de execução concluiu a suspensão de todos os threads de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="251d1-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="251d1-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="251d1-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="251d1-105">Remarks</span></span>  
 <span data-ttu-id="251d1-106">Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar em execução até tentarem inserir novamente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="251d1-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="251d1-107">Nesse ponto, eles também serão suspensos até que o tempo de execução seja retomado.</span><span class="sxs-lookup"><span data-stu-id="251d1-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="251d1-108">Isso também se aplica a novos threads que entram no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="251d1-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="251d1-109">Todos os threads no tempo de execução serão suspensos imediatamente se já estiverem no código passível de interrupção ou se forem solicitados a suspender quando acessarem o código passível de interrupção.</span><span class="sxs-lookup"><span data-stu-id="251d1-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="251d1-110">`RuntimeSuspendFinished`É garantido que o retorno de chamada ocorra no mesmo thread que o retorno de chamada [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="251d1-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251d1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="251d1-111">Requirements</span></span>  
 <span data-ttu-id="251d1-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="251d1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251d1-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="251d1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="251d1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="251d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="251d1-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="251d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251d1-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="251d1-116">See also</span></span>

- [<span data-ttu-id="251d1-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="251d1-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="251d1-118">Método RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="251d1-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
