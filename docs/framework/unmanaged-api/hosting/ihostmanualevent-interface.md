---
title: Interface IHostManualEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent
helpviewer_keywords: IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c19125d96d5f4a9e91fc083d53f36ebebd2c569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="5f24f-102">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="5f24f-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="5f24f-103">Fornece a implementação do host de uma representação de um evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="5f24f-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f24f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5f24f-104">Methods</span></span>  
  
|<span data-ttu-id="5f24f-105">Método</span><span class="sxs-lookup"><span data-stu-id="5f24f-105">Method</span></span>|<span data-ttu-id="5f24f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f24f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f24f-107">Método Reset</span><span class="sxs-lookup"><span data-stu-id="5f24f-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="5f24f-108">Redefine o atual `IHostManualEvent` instância para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="5f24f-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="5f24f-109">Método Set</span><span class="sxs-lookup"><span data-stu-id="5f24f-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="5f24f-110">Define o atual `IHostManualEvent` instância para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="5f24f-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="5f24f-111">Método Wait</span><span class="sxs-lookup"><span data-stu-id="5f24f-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="5f24f-112">Faz com que o atual `IHostManualEvent` instância para aguardar até que ele pertence, ou um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="5f24f-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f24f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f24f-113">Requirements</span></span>  
 <span data-ttu-id="5f24f-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f24f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f24f-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f24f-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f24f-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5f24f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f24f-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f24f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f24f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f24f-118">See Also</span></span>  
 [<span data-ttu-id="5f24f-119">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="5f24f-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="5f24f-120">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="5f24f-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="5f24f-121">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="5f24f-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="5f24f-122">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="5f24f-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="5f24f-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5f24f-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
