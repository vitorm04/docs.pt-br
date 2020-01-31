---
title: Método ICorProfilerCallback::RuntimeSuspendStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865877"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="675cd-102">Método ICorProfilerCallback::RuntimeSuspendStarted</span><span class="sxs-lookup"><span data-stu-id="675cd-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="675cd-103">Notifica o criador de perfil que o tempo de execução está prestes a suspender todos os threads de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="675cd-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="675cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="675cd-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="675cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="675cd-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="675cd-106">no Um valor da enumeração [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) que indica o motivo da suspensão.</span><span class="sxs-lookup"><span data-stu-id="675cd-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="675cd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="675cd-107">Remarks</span></span>  
 <span data-ttu-id="675cd-108">Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar em execução até tentarem inserir novamente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="675cd-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="675cd-109">Nesse ponto, eles também serão suspensos até que o tempo de execução seja retomado.</span><span class="sxs-lookup"><span data-stu-id="675cd-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="675cd-110">Isso também se aplica a novos threads que entram no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="675cd-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="675cd-111">Todos os threads no tempo de execução serão suspensos imediatamente se já estiverem no código passível de interrupção ou se forem solicitados a suspender quando acessarem o código passível de interrupção.</span><span class="sxs-lookup"><span data-stu-id="675cd-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="675cd-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="675cd-112">Requirements</span></span>  
 <span data-ttu-id="675cd-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="675cd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="675cd-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="675cd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="675cd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="675cd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="675cd-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="675cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675cd-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="675cd-117">See also</span></span>

- [<span data-ttu-id="675cd-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="675cd-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="675cd-119">Método RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="675cd-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="675cd-120">Método RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="675cd-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
