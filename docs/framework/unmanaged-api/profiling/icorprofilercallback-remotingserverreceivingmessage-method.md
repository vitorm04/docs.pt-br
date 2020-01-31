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
ms.openlocfilehash: 6e045a99de9ad30516fd12a7b490e26c860bde7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866007"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="013ea-102">Método ICorProfilerCallback::RemotingServerReceivingMessage</span><span class="sxs-lookup"><span data-stu-id="013ea-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="013ea-103">Notifica o criador de perfil de que o processo recebeu uma invocação de método remoto ou uma solicitação de ativação.</span><span class="sxs-lookup"><span data-stu-id="013ea-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="013ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="013ea-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="013ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="013ea-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="013ea-106">no Um valor que corresponderá com o valor fornecido em [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="013ea-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="013ea-107">Os cookies de GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="013ea-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="013ea-108">O canal tem sucesso ao transmitir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="013ea-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="013ea-109">Os cookies de GUID estão ativos no processo do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="013ea-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="013ea-110">Isso permite um emparelhamento fácil de chamadas remotas e a criação de uma pilha de chamadas lógica.</span><span class="sxs-lookup"><span data-stu-id="013ea-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="013ea-111">no Um valor que será `true` se a chamada for assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="013ea-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="013ea-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="013ea-112">Remarks</span></span>  
 <span data-ttu-id="013ea-113">Se a solicitação de mensagem for assíncrona, a solicitação poderá ser atendida por qualquer thread arbitrário.</span><span class="sxs-lookup"><span data-stu-id="013ea-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013ea-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="013ea-114">Requirements</span></span>  
 <span data-ttu-id="013ea-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="013ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="013ea-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="013ea-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="013ea-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="013ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="013ea-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="013ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013ea-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="013ea-119">See also</span></span>

- [<span data-ttu-id="013ea-120">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="013ea-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
