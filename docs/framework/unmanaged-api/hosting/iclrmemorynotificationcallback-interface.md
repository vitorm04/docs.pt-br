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
ms.openlocfilehash: 6b998f8af2c7f4add3ecbb905928b5956409bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="9e818-102">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="9e818-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="9e818-103">Permite que o host para condições de pressão de memória do relatório usando uma abordagem semelhante do Win32 `CreateMemoryResourceNotification` função.</span><span class="sxs-lookup"><span data-stu-id="9e818-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e818-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9e818-104">Methods</span></span>  
  
|<span data-ttu-id="9e818-105">Método</span><span class="sxs-lookup"><span data-stu-id="9e818-105">Method</span></span>|<span data-ttu-id="9e818-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e818-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e818-107">Método OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="9e818-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="9e818-108">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="9e818-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e818-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e818-109">Remarks</span></span>  
 <span data-ttu-id="9e818-110">O host usa a `ICLRMemoryNotificationCallback` interface para solicitar que o CLR liberar recursos de memória.</span><span class="sxs-lookup"><span data-stu-id="9e818-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e818-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e818-111">Requirements</span></span>  
 <span data-ttu-id="9e818-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e818-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e818-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e818-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e818-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9e818-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e818-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e818-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e818-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e818-116">See Also</span></span>  
 [<span data-ttu-id="9e818-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="9e818-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="9e818-118">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="9e818-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
