---
title: Interface IHostSemaphore
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bcc6a9a7847932e9e469cdbffc9792e1d5860570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="1371a-102">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="1371a-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="1371a-103">Representa a implementação do host de um sinal de threading.</span><span class="sxs-lookup"><span data-stu-id="1371a-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1371a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1371a-104">Methods</span></span>  
  
|<span data-ttu-id="1371a-105">Método</span><span class="sxs-lookup"><span data-stu-id="1371a-105">Method</span></span>|<span data-ttu-id="1371a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1371a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1371a-107">Método ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="1371a-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="1371a-108">Aumenta a contagem do atual `IHostSemaphore` instância pelo valor especificado.</span><span class="sxs-lookup"><span data-stu-id="1371a-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="1371a-109">Método Wait</span><span class="sxs-lookup"><span data-stu-id="1371a-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="1371a-110">Faz com que o atual `IHostSemaphore` instância para aguardar até que ele é de propriedade ou o período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="1371a-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1371a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1371a-111">Requirements</span></span>  
 <span data-ttu-id="1371a-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1371a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1371a-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1371a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1371a-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1371a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1371a-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1371a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1371a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1371a-116">See Also</span></span>  
 [<span data-ttu-id="1371a-117">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="1371a-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1371a-118">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="1371a-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="1371a-119">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="1371a-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="1371a-120">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="1371a-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="1371a-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="1371a-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
