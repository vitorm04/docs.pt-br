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
ms.openlocfilehash: 8a042e71690b5ae77c1e4cda7be394a163ab2774
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503257"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="0967b-102">Método ICorProfilerCallback::RemotingClientInvocationStarted</span><span class="sxs-lookup"><span data-stu-id="0967b-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="0967b-103">Notifica o criador de perfil de que uma chamada de comunicação remota foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="0967b-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0967b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0967b-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0967b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="0967b-105">Remarks</span></span>  
 <span data-ttu-id="0967b-106">Esse evento é o mesmo para chamadas síncronas e assíncronas.</span><span class="sxs-lookup"><span data-stu-id="0967b-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="0967b-107">Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:</span><span class="sxs-lookup"><span data-stu-id="0967b-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="0967b-108">`RemotingClientInvocationStarted`e [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="0967b-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="0967b-109">[ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) e [ICorProfilerCallback:: RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="0967b-109">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="0967b-110">[ICorProfilerCallback:: RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) e [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="0967b-110">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="0967b-111">Você deve estar ciente dos seguintes problemas com os retornos de chamada remotos:</span><span class="sxs-lookup"><span data-stu-id="0967b-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="0967b-112">A execução de uma função de comunicação remota não é refletida pela API do criador de perfil, portanto, as notificações para funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="0967b-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="0967b-113">A invocação real ocorre por meio de um objeto proxy; para o criador de perfil, parece que determinadas funções são compiladas por JIT, mas nunca são usadas.</span><span class="sxs-lookup"><span data-stu-id="0967b-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="0967b-114">O criador de perfil não recebe notificações precisas para eventos de comunicação remota assíncrona.</span><span class="sxs-lookup"><span data-stu-id="0967b-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0967b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0967b-115">Requirements</span></span>  
 <span data-ttu-id="0967b-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0967b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0967b-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0967b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0967b-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0967b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0967b-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0967b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0967b-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="0967b-120">See also</span></span>

- [<span data-ttu-id="0967b-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0967b-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
