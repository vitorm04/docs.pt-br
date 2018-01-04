---
title: Interface ICLRMemoryNotificationCallback
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback
helpviewer_keywords: ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc09e3668dc814360de0256c2476ffa7b61462ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="e188c-102">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="e188c-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="e188c-103">Permite que o host para condições de pressão de memória do relatório usando uma abordagem semelhante do Win32 `CreateMemoryResourceNotification` função.</span><span class="sxs-lookup"><span data-stu-id="e188c-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e188c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e188c-104">Methods</span></span>  
  
|<span data-ttu-id="e188c-105">Método</span><span class="sxs-lookup"><span data-stu-id="e188c-105">Method</span></span>|<span data-ttu-id="e188c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e188c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e188c-107">Método OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="e188c-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="e188c-108">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="e188c-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e188c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e188c-109">Remarks</span></span>  
 <span data-ttu-id="e188c-110">O host usa a `ICLRMemoryNotificationCallback` interface para solicitar que o CLR liberar recursos de memória.</span><span class="sxs-lookup"><span data-stu-id="e188c-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e188c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e188c-111">Requirements</span></span>  
 <span data-ttu-id="e188c-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e188c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e188c-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e188c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e188c-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e188c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e188c-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e188c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e188c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e188c-116">See Also</span></span>  
 [<span data-ttu-id="e188c-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="e188c-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="e188c-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e188c-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
