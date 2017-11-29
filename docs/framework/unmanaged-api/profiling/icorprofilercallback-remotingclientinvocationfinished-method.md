---
title: "Método ICorProfilerCallback::RemotingClientInvocationFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77f86d12d3a19f1b02ece35c8b717e78802f74f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="2edee-102">Método ICorProfilerCallback::RemotingClientInvocationFinished</span><span class="sxs-lookup"><span data-stu-id="2edee-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="2edee-103">Notifica o criador de perfil que uma chamada de comunicação remota foi executado para conclusão no cliente.</span><span class="sxs-lookup"><span data-stu-id="2edee-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2edee-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2edee-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2edee-105">Remarks</span></span>  
 <span data-ttu-id="2edee-106">Se a chamada de comunicação remota síncrona, ele também foi executada até a conclusão no servidor.</span><span class="sxs-lookup"><span data-stu-id="2edee-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="2edee-107">Se a chamada de comunicação remota assíncrona, uma resposta ainda poderia ser esperada quando a chamada é manipulada.</span><span class="sxs-lookup"><span data-stu-id="2edee-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="2edee-108">Se uma resposta é esperada, ocorrerá uma chamada para [: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e uma chamada adicional para `RemotingClientInvocationFinished` para indicar o processamento necessário secundário de uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2edee-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="2edee-109">Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:</span><span class="sxs-lookup"><span data-stu-id="2edee-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="2edee-110">`RemotingClientInvocationStarted`e [: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="2edee-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="2edee-111">[: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e [: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="2edee-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="2edee-112">[Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) e [: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="2edee-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="2edee-113">Você deve estar ciente dos problemas a seguir com os retornos de chamada de comunicação remota:</span><span class="sxs-lookup"><span data-stu-id="2edee-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="2edee-114">Execução de uma função de comunicação remota não é refletida pela API, o criador de perfil para que as notificações para as funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="2edee-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="2edee-115">A invocação real ocorre por meio de um objeto de proxy. o criador de perfil, parece que determinadas funções são compilados JIT, mas nunca é usado.</span><span class="sxs-lookup"><span data-stu-id="2edee-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="2edee-116">O criador de perfil não recebe notificações precisas para eventos de comunicação remota assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2edee-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2edee-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2edee-117">Requirements</span></span>  
 <span data-ttu-id="2edee-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2edee-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2edee-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2edee-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2edee-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2edee-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2edee-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2edee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edee-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2edee-122">See Also</span></span>  
 [<span data-ttu-id="2edee-123">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="2edee-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
