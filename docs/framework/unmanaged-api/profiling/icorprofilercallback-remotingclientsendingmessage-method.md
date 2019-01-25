---
title: Método ICorProfilerCallback::RemotingClientSendingMessage
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 424e0323c018367560d4cf3542e9e8668575a03f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675143"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="0cea0-102">Método ICorProfilerCallback::RemotingClientSendingMessage</span><span class="sxs-lookup"><span data-stu-id="0cea0-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="0cea0-103">Notifica o criador de perfil que o cliente está enviando uma solicitação ao servidor.</span><span class="sxs-lookup"><span data-stu-id="0cea0-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cea0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cea0-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0cea0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0cea0-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="0cea0-106">[in] Um valor que corresponde com o valor fornecido no [ICorProfilerCallback:: Remotingserverreceivingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="0cea0-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="0cea0-107">Cookies GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="0cea0-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="0cea0-108">O canal é bem-sucedida na transmissão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0cea0-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="0cea0-109">Os cookies GUID são Active Directory sobre o processo do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="0cea0-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="0cea0-110">Isso permite que o emparelhamento fácil de chamadas de comunicação remota e a criação de uma pilha de chamadas lógicas.</span><span class="sxs-lookup"><span data-stu-id="0cea0-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="0cea0-111">[in] Um valor que é `true` se a chamada é assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0cea0-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cea0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0cea0-112">Requirements</span></span>  
 <span data-ttu-id="0cea0-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cea0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cea0-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0cea0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0cea0-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cea0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cea0-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cea0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cea0-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cea0-117">See also</span></span>
- [<span data-ttu-id="0cea0-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0cea0-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
