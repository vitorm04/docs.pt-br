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
ms.openlocfilehash: 157e6bc6cb9603fa9558ad6d39f0b086849fc7b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499890"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="4b217-102">Método ICorProfilerCallback::RemotingServerReceivingMessage</span><span class="sxs-lookup"><span data-stu-id="4b217-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="4b217-103">Notifica o criador de perfil de que o processo recebeu uma invocação de método remoto ou uma solicitação de ativação.</span><span class="sxs-lookup"><span data-stu-id="4b217-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b217-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b217-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b217-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b217-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="4b217-106">no Um valor que corresponderá com o valor fornecido em [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="4b217-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="4b217-107">Os cookies de GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="4b217-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="4b217-108">O canal tem sucesso ao transmitir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="4b217-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="4b217-109">Os cookies de GUID estão ativos no processo do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="4b217-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="4b217-110">Isso permite um emparelhamento fácil de chamadas remotas e a criação de uma pilha de chamadas lógica.</span><span class="sxs-lookup"><span data-stu-id="4b217-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="4b217-111">no Um valor que é `true` se a chamada for assíncrona; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="4b217-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b217-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b217-112">Remarks</span></span>  
 <span data-ttu-id="4b217-113">Se a solicitação de mensagem for assíncrona, a solicitação poderá ser atendida por qualquer thread arbitrário.</span><span class="sxs-lookup"><span data-stu-id="4b217-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b217-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b217-114">Requirements</span></span>  
 <span data-ttu-id="4b217-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b217-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b217-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4b217-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b217-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b217-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b217-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b217-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b217-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="4b217-119">See also</span></span>

- [<span data-ttu-id="4b217-120">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4b217-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
