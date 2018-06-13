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
ms.openlocfilehash: 04956fb5519c66141f4bd7330367f6c78b4e7bc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453952"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="6d2d9-102">Método ICorProfilerCallback::RemotingClientReceivingReply</span><span class="sxs-lookup"><span data-stu-id="6d2d9-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="6d2d9-103">Notifica o criador de perfil que a parte do servidor de uma chamada de comunicação remota foi concluída e o cliente agora está recebendo e prestes a processar a resposta.</span><span class="sxs-lookup"><span data-stu-id="6d2d9-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d2d9-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d2d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d2d9-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="6d2d9-106">[in] Um valor que irá corresponder com o valor fornecido no [: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="6d2d9-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="6d2d9-107">Cookies GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="6d2d9-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="6d2d9-108">O canal tem sucesso na transmissão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6d2d9-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="6d2d9-109">Cookies GUID estão ativos no processo do servidor.</span><span class="sxs-lookup"><span data-stu-id="6d2d9-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="6d2d9-110">Isso permite que o emparelhamento fácil de chamadas de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="6d2d9-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="6d2d9-111">[in] Um valor que é `true` se a chamada for assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6d2d9-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d2d9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d2d9-112">Requirements</span></span>  
 <span data-ttu-id="6d2d9-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2d9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2d9-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d2d9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d2d9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d2d9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d2d9-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2d9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d2d9-117">See Also</span></span>  
 [<span data-ttu-id="6d2d9-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6d2d9-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
