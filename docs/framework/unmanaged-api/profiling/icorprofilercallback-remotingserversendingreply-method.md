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
ms.openlocfilehash: f77901623ef4df7b43276c18a910cf62fcc4451d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865968"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="0f628-102">Método ICorProfilerCallback::RemotingServerSendingReply</span><span class="sxs-lookup"><span data-stu-id="0f628-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="0f628-103">Notifica o criador de perfil de que o processo concluiu o processamento de uma solicitação de invocação de método remoto e está prestes a transmitir a resposta por meio de um canal.</span><span class="sxs-lookup"><span data-stu-id="0f628-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f628-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f628-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f628-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f628-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="0f628-106">no Um ponteiro para um GUID que corresponderá com o valor fornecido em [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) sob estas condições:</span><span class="sxs-lookup"><span data-stu-id="0f628-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="0f628-107">Os cookies de GUID de comunicação remota estão ativos.</span><span class="sxs-lookup"><span data-stu-id="0f628-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="0f628-108">O canal tem sucesso ao transmitir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="0f628-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="0f628-109">Os cookies de GUID estão ativos no processo do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="0f628-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="0f628-110">Isso permite um emparelhamento fácil de chamadas remotas e a criação de uma pilha de chamadas lógica.</span><span class="sxs-lookup"><span data-stu-id="0f628-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="0f628-111">no Um valor que será `true` se a chamada for assíncrona; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0f628-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f628-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0f628-112">Requirements</span></span>  
 <span data-ttu-id="0f628-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f628-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f628-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0f628-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f628-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f628-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f628-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f628-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f628-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="0f628-117">See also</span></span>

- [<span data-ttu-id="0f628-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0f628-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
