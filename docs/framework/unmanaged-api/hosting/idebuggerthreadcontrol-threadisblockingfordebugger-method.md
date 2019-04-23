---
title: Método IDebuggerThreadControl::ThreadIsBlockingForDebugger
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ff178cc9ab798593848e56fc7bba8ac82ae295
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154226"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="4445b-102">Método IDebuggerThreadControl::ThreadIsBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="4445b-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="4445b-103">Notifica o host que o thread que está enviando esse retorno de chamada é sobre como bloquear dentro dos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="4445b-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4445b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4445b-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="4445b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4445b-105">Remarks</span></span>  
 <span data-ttu-id="4445b-106">O `ThreadIsBlockingForDebugger` método sempre será chamado em um segmento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4445b-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="4445b-107">O `ThreadIsBlockingForDebugger` método host uma oportunidade para realizar outra ação enquanto os blocos de thread.</span><span class="sxs-lookup"><span data-stu-id="4445b-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4445b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4445b-108">Requirements</span></span>  
 <span data-ttu-id="4445b-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4445b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4445b-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4445b-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4445b-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4445b-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4445b-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4445b-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4445b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4445b-113">See also</span></span>

- [<span data-ttu-id="4445b-114">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="4445b-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
