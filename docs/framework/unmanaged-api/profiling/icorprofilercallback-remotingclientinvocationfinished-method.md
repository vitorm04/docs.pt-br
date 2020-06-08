---
title: Método ICorProfilerCallback::RemotingClientInvocationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
ms.openlocfilehash: f5786db1f17e8a463dc78f9c93464145be3a8f32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499981"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="fff3b-102">Método ICorProfilerCallback::RemotingClientInvocationFinished</span><span class="sxs-lookup"><span data-stu-id="fff3b-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="fff3b-103">Notifica o criador de perfil de que uma chamada de comunicação remota foi executada até a conclusão no cliente.</span><span class="sxs-lookup"><span data-stu-id="fff3b-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fff3b-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fff3b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="fff3b-105">Remarks</span></span>  
 <span data-ttu-id="fff3b-106">Se a chamada remota tiver sido síncrona, ela também será executada para conclusão no servidor.</span><span class="sxs-lookup"><span data-stu-id="fff3b-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="fff3b-107">Se a chamada remota tiver sido assíncrona, uma resposta ainda poderá ser esperada quando a chamada for tratada.</span><span class="sxs-lookup"><span data-stu-id="fff3b-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="fff3b-108">Se uma resposta for esperada, ela ocorrerá como uma chamada para [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) e uma chamada adicional para `RemotingClientInvocationFinished` para indicar o processamento secundário necessário de uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fff3b-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="fff3b-109">Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:</span><span class="sxs-lookup"><span data-stu-id="fff3b-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="fff3b-110">`RemotingClientInvocationStarted`e [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="fff3b-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="fff3b-111">[ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) e [ICorProfilerCallback:: RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="fff3b-111">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="fff3b-112">[ICorProfilerCallback:: RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) e [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="fff3b-112">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="fff3b-113">Você deve estar ciente dos seguintes problemas com os retornos de chamada remotos:</span><span class="sxs-lookup"><span data-stu-id="fff3b-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="fff3b-114">A execução de uma função de comunicação remota não é refletida pela API do criador de perfil, portanto, as notificações para funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="fff3b-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="fff3b-115">A invocação real ocorre por meio de um objeto proxy; para o criador de perfil, parece que determinadas funções são compiladas por JIT, mas nunca são usadas.</span><span class="sxs-lookup"><span data-stu-id="fff3b-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="fff3b-116">O criador de perfil não recebe notificações precisas para eventos de comunicação remota assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fff3b-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff3b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fff3b-117">Requirements</span></span>  
 <span data-ttu-id="fff3b-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fff3b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff3b-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fff3b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fff3b-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fff3b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fff3b-121">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff3b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff3b-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="fff3b-122">See also</span></span>

- [<span data-ttu-id="fff3b-123">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="fff3b-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
