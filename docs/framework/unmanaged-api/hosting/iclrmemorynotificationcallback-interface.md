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
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948536"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="9fae8-102">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="9fae8-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="9fae8-103">Permite que o host para condições de pressão de memória de relatório usando uma abordagem semelhante do Win32 `CreateMemoryResourceNotification` função.</span><span class="sxs-lookup"><span data-stu-id="9fae8-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9fae8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9fae8-104">Methods</span></span>  
  
|<span data-ttu-id="9fae8-105">Método</span><span class="sxs-lookup"><span data-stu-id="9fae8-105">Method</span></span>|<span data-ttu-id="9fae8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fae8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fae8-107">Método OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="9fae8-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="9fae8-108">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="9fae8-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fae8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fae8-109">Remarks</span></span>  
 <span data-ttu-id="9fae8-110">O host usa o `ICLRMemoryNotificationCallback` interface para solicitar que o CLR libere os recursos de memória.</span><span class="sxs-lookup"><span data-stu-id="9fae8-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fae8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fae8-111">Requirements</span></span>  
 <span data-ttu-id="9fae8-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fae8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fae8-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9fae8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fae8-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9fae8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fae8-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fae8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fae8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fae8-116">See also</span></span>

- [<span data-ttu-id="9fae8-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="9fae8-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="9fae8-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="9fae8-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
