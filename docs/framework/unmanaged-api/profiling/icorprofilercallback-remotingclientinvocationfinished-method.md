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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2722497db5622dee4adcfd9381837477b89a8f63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206571"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="2f7b5-102">Método ICorProfilerCallback::RemotingClientInvocationFinished</span><span class="sxs-lookup"><span data-stu-id="2f7b5-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="2f7b5-103">Notifica o criador de perfil que uma chamada de comunicação remota foi executado até a conclusão no cliente.</span><span class="sxs-lookup"><span data-stu-id="2f7b5-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f7b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f7b5-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2f7b5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f7b5-105">Remarks</span></span>  
 <span data-ttu-id="2f7b5-106">Se a chamada de comunicação remota síncrona, ele também foi executada até a conclusão no servidor.</span><span class="sxs-lookup"><span data-stu-id="2f7b5-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="2f7b5-107">Se a chamada de comunicação remota foi assíncrona, uma resposta ainda pode ser esperada quando a chamada é manipulada.</span><span class="sxs-lookup"><span data-stu-id="2f7b5-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="2f7b5-108">Se uma resposta é esperada, ocorrerá como uma chamada para [ICorProfilerCallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e uma chamada adicional para `RemotingClientInvocationFinished` para indicar o processamento necessário secundário de uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2f7b5-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="2f7b5-109">Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:</span><span class="sxs-lookup"><span data-stu-id="2f7b5-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="2f7b5-110">`RemotingClientInvocationStarted` e [ICorProfilerCallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="2f7b5-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="2f7b5-111">[ICorProfilerCallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e [ICorProfilerCallback:: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="2f7b5-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="2f7b5-112">[ICorProfilerCallback:: Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) e [ICorProfilerCallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="2f7b5-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="2f7b5-113">Você deve estar ciente dos seguintes problemas com os retornos de chamada de comunicação remota:</span><span class="sxs-lookup"><span data-stu-id="2f7b5-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="2f7b5-114">Execução de uma função de comunicação remota não é refletida pelo criador de perfil API, portanto, as notificações para as funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="2f7b5-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="2f7b5-115">A invocação real ocorre por meio de um objeto de proxy; o criador de perfil, parece que determinadas funções são compilados em JIT, mas nunca usados.</span><span class="sxs-lookup"><span data-stu-id="2f7b5-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="2f7b5-116">O criador de perfil não recebe notificações precisas de eventos de comunicação remota assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2f7b5-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f7b5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f7b5-117">Requirements</span></span>  
 <span data-ttu-id="2f7b5-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f7b5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f7b5-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f7b5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f7b5-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f7b5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f7b5-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f7b5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7b5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f7b5-122">See also</span></span>

- [<span data-ttu-id="2f7b5-123">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="2f7b5-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
