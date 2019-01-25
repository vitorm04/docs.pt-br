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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3167d288a57575af85a9cb50f5c0cd82c8e9cc9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702789"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="314d9-102">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="314d9-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="314d9-103">Permite que o host para condições de pressão de memória de relatório usando uma abordagem semelhante do Win32 `CreateMemoryResourceNotification` função.</span><span class="sxs-lookup"><span data-stu-id="314d9-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="314d9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="314d9-104">Methods</span></span>  
  
|<span data-ttu-id="314d9-105">Método</span><span class="sxs-lookup"><span data-stu-id="314d9-105">Method</span></span>|<span data-ttu-id="314d9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="314d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="314d9-107">Método OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="314d9-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="314d9-108">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="314d9-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="314d9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="314d9-109">Remarks</span></span>  
 <span data-ttu-id="314d9-110">O host usa o `ICLRMemoryNotificationCallback` interface para solicitar que o CLR libere os recursos de memória.</span><span class="sxs-lookup"><span data-stu-id="314d9-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="314d9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="314d9-111">Requirements</span></span>  
 <span data-ttu-id="314d9-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="314d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="314d9-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="314d9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="314d9-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="314d9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="314d9-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="314d9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314d9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="314d9-116">See also</span></span>
- [<span data-ttu-id="314d9-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="314d9-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="314d9-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="314d9-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
