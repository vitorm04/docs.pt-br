---
title: Método ICorProfilerCallback::RemotingServerReceivingMessage
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30015cc6cae935c43cdbfec1a6eeae5c703ef9f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103201"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="064b2-102">Método ICorProfilerCallback::RemotingServerReceivingMessage</span><span class="sxs-lookup"><span data-stu-id="064b2-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="064b2-103">Notifica o criador de perfil que o processo tenha recebido uma solicitação de ativação ou invocação de método remoto.</span><span class="sxs-lookup"><span data-stu-id="064b2-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="064b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="064b2-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="064b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="064b2-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="064b2-106">[in] Um valor que irá corresponder com o valor fornecido no [ICorProfilerCallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="064b2-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="064b2-107">Cookies GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="064b2-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="064b2-108">O canal é bem-sucedida na transmissão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="064b2-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="064b2-109">Os cookies GUID são Active Directory sobre o processo do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="064b2-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="064b2-110">Isso permite que o emparelhamento fácil de chamadas de comunicação remota e a criação de uma pilha de chamadas lógicas.</span><span class="sxs-lookup"><span data-stu-id="064b2-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="064b2-111">[in] Um valor que é `true` se a chamada é assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="064b2-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="064b2-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="064b2-112">Remarks</span></span>  
 <span data-ttu-id="064b2-113">Se a solicitação de mensagem é assíncrona, a solicitação pode ser atendida por qualquer thread arbitrário.</span><span class="sxs-lookup"><span data-stu-id="064b2-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="064b2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="064b2-114">Requirements</span></span>  
 <span data-ttu-id="064b2-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="064b2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="064b2-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="064b2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="064b2-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="064b2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="064b2-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="064b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064b2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="064b2-119">See also</span></span>

- [<span data-ttu-id="064b2-120">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="064b2-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
