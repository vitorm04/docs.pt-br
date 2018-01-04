---
title: "Método ICorProfilerCallback::RemotingServerSendingReply"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerSendingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f8fa5a81231c8181e0d0257a1bbfdb4a1f0a7a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="a73a6-102">Método ICorProfilerCallback::RemotingServerSendingReply</span><span class="sxs-lookup"><span data-stu-id="a73a6-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="a73a6-103">Notifica o criador de perfil que o processo terminou de processar uma solicitação de invocação de método remoto e é a resposta por meio de um canal de transmissão.</span><span class="sxs-lookup"><span data-stu-id="a73a6-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a73a6-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a73a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a73a6-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="a73a6-106">[in] Um ponteiro para um GUID que irá corresponder com o valor fornecido no [: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="a73a6-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="a73a6-107">Cookies GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="a73a6-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="a73a6-108">O canal tem sucesso na transmissão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a73a6-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="a73a6-109">Cookies GUID estão ativos no processo de cliente.</span><span class="sxs-lookup"><span data-stu-id="a73a6-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="a73a6-110">Isso permite que o emparelhamento fácil de chamadas de comunicação remota e a criação de uma pilha de chamadas lógicas.</span><span class="sxs-lookup"><span data-stu-id="a73a6-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="a73a6-111">[in] Um valor que é `true` se a chamada for assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a73a6-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a73a6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a73a6-112">Requirements</span></span>  
 <span data-ttu-id="a73a6-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a73a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a73a6-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a73a6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a73a6-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a73a6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a73a6-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a73a6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73a6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a73a6-117">See Also</span></span>  
 [<span data-ttu-id="a73a6-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a73a6-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
