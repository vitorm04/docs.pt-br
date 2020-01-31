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
ms.openlocfilehash: 8ae58344a7a17637bf08b9b5179abdba7e7060d6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866020"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="32cd4-102">Método ICorProfilerCallback::RemotingClientSendingMessage</span><span class="sxs-lookup"><span data-stu-id="32cd4-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="32cd4-103">Notifica o criador de perfil de que o cliente está enviando uma solicitação para o servidor.</span><span class="sxs-lookup"><span data-stu-id="32cd4-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32cd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32cd4-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32cd4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32cd4-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="32cd4-106">no Um valor que corresponde ao valor fornecido em [ICorProfilerCallback:: RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="32cd4-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="32cd4-107">Os cookies de GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="32cd4-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="32cd4-108">O canal tem sucesso ao transmitir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="32cd4-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="32cd4-109">Os cookies de GUID estão ativos no processo do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="32cd4-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="32cd4-110">Isso permite um emparelhamento fácil de chamadas remotas e a criação de uma pilha de chamadas lógica.</span><span class="sxs-lookup"><span data-stu-id="32cd4-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="32cd4-111">no Um valor que será `true` se a chamada for assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="32cd4-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32cd4-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="32cd4-112">Requirements</span></span>  
 <span data-ttu-id="32cd4-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32cd4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32cd4-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="32cd4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32cd4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32cd4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32cd4-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32cd4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32cd4-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="32cd4-117">See also</span></span>

- [<span data-ttu-id="32cd4-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="32cd4-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
