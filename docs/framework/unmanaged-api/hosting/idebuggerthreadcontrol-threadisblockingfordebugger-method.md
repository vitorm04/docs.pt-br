---
title: "Método IDebuggerThreadControl::ThreadIsBlockingForDebugger"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5b14818f06fec78cfc2cff9ea66548c9ee87bb4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="f804c-102">Método IDebuggerThreadControl::ThreadIsBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="f804c-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="f804c-103">Notifica o host que o thread que está enviando esse retorno de chamada está prestes a bloco entre os serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="f804c-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f804c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f804c-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="f804c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="f804c-105">Remarks</span></span>  
 <span data-ttu-id="f804c-106">O `ThreadIsBlockingForDebugger` método sempre será chamado em um thread de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f804c-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="f804c-107">O `ThreadIsBlockingForDebugger` método host uma oportunidade para executar outra ação enquanto o bloqueia o thread.</span><span class="sxs-lookup"><span data-stu-id="f804c-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f804c-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f804c-108">Requirements</span></span>  
 <span data-ttu-id="f804c-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f804c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f804c-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f804c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f804c-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f804c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f804c-112">**As versões do .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f804c-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f804c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f804c-113">See Also</span></span>  
 [<span data-ttu-id="f804c-114">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="f804c-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
