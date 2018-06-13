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
ms.openlocfilehash: 2c5cf7e17989f3c083c7c4e52fa8cfc09c00bc7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431513"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="baa47-102">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="baa47-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="baa47-103">Permite que o host para condições de pressão de memória do relatório usando uma abordagem semelhante do Win32 `CreateMemoryResourceNotification` função.</span><span class="sxs-lookup"><span data-stu-id="baa47-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="baa47-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="baa47-104">Methods</span></span>  
  
|<span data-ttu-id="baa47-105">Método</span><span class="sxs-lookup"><span data-stu-id="baa47-105">Method</span></span>|<span data-ttu-id="baa47-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="baa47-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="baa47-107">Método OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="baa47-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="baa47-108">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="baa47-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baa47-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="baa47-109">Remarks</span></span>  
 <span data-ttu-id="baa47-110">O host usa a `ICLRMemoryNotificationCallback` interface para solicitar que o CLR liberar recursos de memória.</span><span class="sxs-lookup"><span data-stu-id="baa47-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baa47-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="baa47-111">Requirements</span></span>  
 <span data-ttu-id="baa47-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baa47-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baa47-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="baa47-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baa47-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="baa47-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baa47-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baa47-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa47-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baa47-116">See Also</span></span>  
 [<span data-ttu-id="baa47-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="baa47-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="baa47-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="baa47-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
