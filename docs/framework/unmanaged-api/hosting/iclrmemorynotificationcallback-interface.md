---
title: Interface ICLRMemoryNotificationCallback
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: e980356ad592e137df7d08dadd77431b0e295380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140994"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="ec09b-102">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="ec09b-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="ec09b-103">Permite que o host relate condições de pressão de memória usando uma abordagem semelhante à da função de `CreateMemoryResourceNotification` do Win32.</span><span class="sxs-lookup"><span data-stu-id="ec09b-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec09b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ec09b-104">Methods</span></span>  
  
|<span data-ttu-id="ec09b-105">Método</span><span class="sxs-lookup"><span data-stu-id="ec09b-105">Method</span></span>|<span data-ttu-id="ec09b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec09b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec09b-107">Método OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="ec09b-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="ec09b-108">Notifica o Common Language Runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="ec09b-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec09b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec09b-109">Remarks</span></span>  
 <span data-ttu-id="ec09b-110">O host usa a interface `ICLRMemoryNotificationCallback` para solicitar que os recursos de memória livre do CLR.</span><span class="sxs-lookup"><span data-stu-id="ec09b-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec09b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec09b-111">Requirements</span></span>  
 <span data-ttu-id="ec09b-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec09b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec09b-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ec09b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec09b-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ec09b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec09b-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec09b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec09b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec09b-116">See also</span></span>

- [<span data-ttu-id="ec09b-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="ec09b-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="ec09b-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ec09b-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
