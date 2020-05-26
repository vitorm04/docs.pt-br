---
title: Interface IHostSemaphore
ms.date: 03/30/2017
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
ms.openlocfilehash: 8345d85502087568cb05dd262cccf181e3ca07ac
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803701"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="ce612-102">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="ce612-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="ce612-103">Representa a implementação do host de um semáforo para Threading.</span><span class="sxs-lookup"><span data-stu-id="ce612-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce612-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ce612-104">Methods</span></span>  
  
|<span data-ttu-id="ce612-105">Método</span><span class="sxs-lookup"><span data-stu-id="ce612-105">Method</span></span>|<span data-ttu-id="ce612-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce612-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce612-107">Método ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="ce612-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="ce612-108">Aumenta a contagem da instância atual `IHostSemaphore` pelo valor especificado.</span><span class="sxs-lookup"><span data-stu-id="ce612-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="ce612-109">Método Wait</span><span class="sxs-lookup"><span data-stu-id="ce612-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="ce612-110">Faz com que a `IHostSemaphore` instância atual aguarde até que ela seja propriedade ou a quantidade especificada de tempo decorre.</span><span class="sxs-lookup"><span data-stu-id="ce612-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce612-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce612-111">Requirements</span></span>  
 <span data-ttu-id="ce612-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce612-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce612-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce612-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce612-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ce612-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce612-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce612-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce612-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce612-116">See also</span></span>

- [<span data-ttu-id="ce612-117">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="ce612-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="ce612-118">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="ce612-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="ce612-119">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="ce612-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="ce612-120">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="ce612-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="ce612-121">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="ce612-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
