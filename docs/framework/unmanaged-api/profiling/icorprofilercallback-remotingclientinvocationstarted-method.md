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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b452cbfc5564d98b3770c2ed97f8453296f0fc13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157684"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="5b271-102">Método ICorProfilerCallback::RemotingClientInvocationStarted</span><span class="sxs-lookup"><span data-stu-id="5b271-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="5b271-103">Notifica o criador de perfil que uma chamada de comunicação remota foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="5b271-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b271-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b271-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5b271-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b271-105">Remarks</span></span>  
 <span data-ttu-id="5b271-106">Esse evento é o mesmo para chamadas síncronas e assíncronas.</span><span class="sxs-lookup"><span data-stu-id="5b271-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="5b271-107">Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:</span><span class="sxs-lookup"><span data-stu-id="5b271-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   `RemotingClientInvocationStarted` <span data-ttu-id="5b271-108">e [ICorProfilerCallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="5b271-108">and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="5b271-109">[ICorProfilerCallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e [ICorProfilerCallback:: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="5b271-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="5b271-110">[ICorProfilerCallback:: Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) e [ICorProfilerCallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="5b271-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="5b271-111">Você deve estar ciente dos seguintes problemas com os retornos de chamada de comunicação remota:</span><span class="sxs-lookup"><span data-stu-id="5b271-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="5b271-112">Execução de uma função de comunicação remota não é refletida pelo criador de perfil API, portanto, as notificações para as funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="5b271-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="5b271-113">A invocação real ocorre por meio de um objeto de proxy; o criador de perfil, parece que determinadas funções são compilados em JIT, mas nunca usados.</span><span class="sxs-lookup"><span data-stu-id="5b271-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="5b271-114">O criador de perfil não recebe notificações precisas de eventos de comunicação remota assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5b271-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b271-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b271-115">Requirements</span></span>  
 <span data-ttu-id="5b271-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b271-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b271-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b271-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b271-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b271-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5b271-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5b271-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b271-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b271-120">See also</span></span>

- [<span data-ttu-id="5b271-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5b271-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
