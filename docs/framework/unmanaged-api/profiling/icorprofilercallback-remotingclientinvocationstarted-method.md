---
title: Método ICorProfilerCallback::RemotingClientInvocationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
ms.openlocfilehash: 5de291774f1e20b4c399c416f9f52657fa8a9a84
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445820"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="fb71a-102">Método ICorProfilerCallback::RemotingClientInvocationStarted</span><span class="sxs-lookup"><span data-stu-id="fb71a-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="fb71a-103">Notifica o criador de perfil de que uma chamada de comunicação remota foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="fb71a-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb71a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb71a-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fb71a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb71a-105">Remarks</span></span>  
 <span data-ttu-id="fb71a-106">Esse evento é o mesmo para chamadas síncronas e assíncronas.</span><span class="sxs-lookup"><span data-stu-id="fb71a-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="fb71a-107">Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:</span><span class="sxs-lookup"><span data-stu-id="fb71a-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="fb71a-108">`RemotingClientInvocationStarted` e [ICorProfilerCallback:: RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="fb71a-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="fb71a-109">[ICorProfilerCallback:: RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e [ICorProfilerCallback:: RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="fb71a-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="fb71a-110">[ICorProfilerCallback:: RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) e [ICorProfilerCallback:: RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="fb71a-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="fb71a-111">Você deve estar ciente dos seguintes problemas com os retornos de chamada remotos:</span><span class="sxs-lookup"><span data-stu-id="fb71a-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="fb71a-112">A execução de uma função de comunicação remota não é refletida pela API do criador de perfil, portanto, as notificações para funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="fb71a-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="fb71a-113">A invocação real ocorre por meio de um objeto proxy; para o criador de perfil, parece que determinadas funções são compiladas por JIT, mas nunca são usadas.</span><span class="sxs-lookup"><span data-stu-id="fb71a-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="fb71a-114">O criador de perfil não recebe notificações precisas para eventos de comunicação remota assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fb71a-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb71a-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb71a-115">Requirements</span></span>  
 <span data-ttu-id="fb71a-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb71a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb71a-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fb71a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb71a-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb71a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb71a-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb71a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb71a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb71a-120">See also</span></span>

- [<span data-ttu-id="fb71a-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="fb71a-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
