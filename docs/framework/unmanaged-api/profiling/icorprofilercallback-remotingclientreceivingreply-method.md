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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5865935af96260982d47b778d208f4235f6245e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164912"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="f2af2-102">Método ICorProfilerCallback::RemotingClientReceivingReply</span><span class="sxs-lookup"><span data-stu-id="f2af2-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="f2af2-103">Notifica o criador de perfil que a parte do lado do servidor de uma chamada de comunicação remota foi concluída e o cliente agora está recebendo e prestes a processar a resposta.</span><span class="sxs-lookup"><span data-stu-id="f2af2-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2af2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2af2-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="f2af2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2af2-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="f2af2-106">[in] Um valor que irá corresponder com o valor fornecido no [ICorProfilerCallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="f2af2-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="f2af2-107">Cookies GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="f2af2-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="f2af2-108">O canal é bem-sucedida na transmissão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f2af2-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="f2af2-109">Os cookies GUID são Active Directory sobre o processo do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="f2af2-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="f2af2-110">Isso permite que o emparelhamento fácil de chamadas de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="f2af2-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f2af2-111">[in] Um valor que é `true` se a chamada é assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f2af2-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2af2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2af2-112">Requirements</span></span>  
 <span data-ttu-id="f2af2-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2af2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2af2-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2af2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2af2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2af2-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f2af2-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f2af2-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2af2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2af2-117">See also</span></span>

- [<span data-ttu-id="f2af2-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f2af2-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
