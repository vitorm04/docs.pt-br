---
title: Método ICorProfilerCallback::RemotingClientReceivingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175129"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="e6060-102">Método ICorProfilerCallback::RemotingClientReceivingReply</span><span class="sxs-lookup"><span data-stu-id="e6060-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="e6060-103">Notifica o profiler que a parte do lado do servidor de uma chamada remoting foi concluída e o cliente está recebendo e prestes a processar a resposta.</span><span class="sxs-lookup"><span data-stu-id="e6060-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6060-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6060-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="e6060-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6060-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="e6060-106">[em] Um valor que corresponderá ao valor fornecido no [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) nessas condições:</span><span class="sxs-lookup"><span data-stu-id="e6060-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="e6060-107">Os cookies GUID de remoção estão ativos.</span><span class="sxs-lookup"><span data-stu-id="e6060-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="e6060-108">O canal consegue transmitir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="e6060-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="e6060-109">Os cookies GUID estão ativos no processo do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="e6060-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="e6060-110">Isso permite um emparelhamento fácil de chamadas remoting.</span><span class="sxs-lookup"><span data-stu-id="e6060-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="e6060-111">[em] Um valor `true` que é se a chamada for assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e6060-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6060-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6060-112">Requirements</span></span>  
 <span data-ttu-id="e6060-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6060-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6060-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6060-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6060-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6060-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6060-116">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6060-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6060-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="e6060-117">See also</span></span>

- [<span data-ttu-id="e6060-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e6060-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
