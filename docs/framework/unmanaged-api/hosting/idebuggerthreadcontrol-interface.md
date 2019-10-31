---
title: Interface IDebuggerThreadControl
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: a65f9f0f29a43cf3d26b4b2bc5f6f594f0557009
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133166"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="6442d-102">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="6442d-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="6442d-103">Fornece métodos para notificar o host sobre o bloqueio e o desbloqueio de threads pelos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="6442d-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6442d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6442d-104">Methods</span></span>  
  
|<span data-ttu-id="6442d-105">Método</span><span class="sxs-lookup"><span data-stu-id="6442d-105">Method</span></span>|<span data-ttu-id="6442d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6442d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6442d-107">Método ThreadIsBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="6442d-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="6442d-108">Notifica o host que o thread que está enviando esse retorno de chamada está prestes a ser bloqueado nos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="6442d-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="6442d-109">Método ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="6442d-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="6442d-110">Notifica o host de que os serviços de depuração estão prestes a liberar todos os threads bloqueados.</span><span class="sxs-lookup"><span data-stu-id="6442d-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="6442d-111">Método StartBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="6442d-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="6442d-112">Notifica o host de que os serviços de depuração estão prestes a começar a bloquear todos os threads.</span><span class="sxs-lookup"><span data-stu-id="6442d-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6442d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6442d-113">Requirements</span></span>  
 <span data-ttu-id="6442d-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6442d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6442d-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6442d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6442d-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6442d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6442d-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6442d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6442d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6442d-118">See also</span></span>

- [<span data-ttu-id="6442d-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="6442d-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
