---
title: Método ICorProfilerCallback::RemotingServerSendingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 024b1f3f7e08dc21582789de7f3899e8e44d5e39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162679"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="33baa-102">Método ICorProfilerCallback::RemotingServerSendingReply</span><span class="sxs-lookup"><span data-stu-id="33baa-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="33baa-103">Notifica o criador de perfil que o processo terminou de processar uma solicitação de invocação de método remoto e está prestes a transmitir a resposta por meio de um canal.</span><span class="sxs-lookup"><span data-stu-id="33baa-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33baa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33baa-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33baa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="33baa-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="33baa-106">[in] Um ponteiro para um GUID que irá corresponder com o valor fornecido no [ICorProfilerCallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="33baa-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="33baa-107">Cookies GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="33baa-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="33baa-108">O canal é bem-sucedida na transmissão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="33baa-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="33baa-109">Os cookies GUID são Active Directory sobre o processo do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="33baa-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="33baa-110">Isso permite que o emparelhamento fácil de chamadas de comunicação remota e a criação de uma pilha de chamadas lógicas.</span><span class="sxs-lookup"><span data-stu-id="33baa-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="33baa-111">[in] Um valor que é `true` se a chamada é assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="33baa-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33baa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33baa-112">Requirements</span></span>  
 <span data-ttu-id="33baa-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33baa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33baa-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33baa-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33baa-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33baa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33baa-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33baa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33baa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33baa-117">See also</span></span>

- [<span data-ttu-id="33baa-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="33baa-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
