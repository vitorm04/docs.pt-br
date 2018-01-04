---
title: Interface IDebuggerThreadControl
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IDebuggerThreadControl
helpviewer_keywords: IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 297a66f9466b00dec4d32f7d8a6e2bd13b6e5655
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="a284f-102">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="a284f-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="a284f-103">Fornece métodos para notificar o host sobre o bloqueio e desbloqueio de threads pelos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="a284f-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a284f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a284f-104">Methods</span></span>  
  
|<span data-ttu-id="a284f-105">Método</span><span class="sxs-lookup"><span data-stu-id="a284f-105">Method</span></span>|<span data-ttu-id="a284f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a284f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a284f-107">Método ThreadIsBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="a284f-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="a284f-108">Notifica o host que o thread que está enviando esse retorno de chamada está prestes a bloco entre os serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="a284f-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="a284f-109">Método ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="a284f-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="a284f-110">Notifica o host que os serviços de depuração estão prestes a liberar todos os threads que estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="a284f-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="a284f-111">Método StartBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="a284f-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="a284f-112">Notifica o host que os serviços de depuração estão prestes a começar a bloquear todos os threads.</span><span class="sxs-lookup"><span data-stu-id="a284f-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a284f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a284f-113">Requirements</span></span>  
 <span data-ttu-id="a284f-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a284f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a284f-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a284f-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a284f-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a284f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a284f-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a284f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a284f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a284f-118">See Also</span></span>  
 [<span data-ttu-id="a284f-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="a284f-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
