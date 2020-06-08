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
ms.openlocfilehash: 820a37c8ca16f4962bf1d72b1f0f404cffd92a1a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499955"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="fe272-102">Método ICorProfilerCallback::RemotingClientSendingMessage</span><span class="sxs-lookup"><span data-stu-id="fe272-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="fe272-103">Notifica o criador de perfil de que o cliente está enviando uma solicitação para o servidor.</span><span class="sxs-lookup"><span data-stu-id="fe272-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe272-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe272-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe272-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe272-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="fe272-106">no Um valor que corresponde ao valor fornecido em [ICorProfilerCallback:: RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="fe272-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="fe272-107">Os cookies de GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="fe272-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="fe272-108">O canal tem sucesso ao transmitir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="fe272-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="fe272-109">Os cookies de GUID estão ativos no processo do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="fe272-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="fe272-110">Isso permite um emparelhamento fácil de chamadas remotas e a criação de uma pilha de chamadas lógica.</span><span class="sxs-lookup"><span data-stu-id="fe272-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="fe272-111">no Um valor que é `true` se a chamada for assíncrona; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="fe272-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe272-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe272-112">Requirements</span></span>  
 <span data-ttu-id="fe272-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe272-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe272-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fe272-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe272-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe272-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe272-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe272-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe272-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe272-117">See also</span></span>

- [<span data-ttu-id="fe272-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="fe272-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
