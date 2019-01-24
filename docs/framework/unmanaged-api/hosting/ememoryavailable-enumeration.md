---
title: Enumeração EMemoryAvailable
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0ffb85dc5f321e45432d6c2fa9448919957f0e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665195"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="fc497-102">Enumeração EMemoryAvailable</span><span class="sxs-lookup"><span data-stu-id="fc497-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="fc497-103">Contém valores que indicam a quantidade de memória física livre no computador.</span><span class="sxs-lookup"><span data-stu-id="fc497-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="fc497-104">Esses valores são mapeados logicamente para os eventos de alta e baixa memória retornado do `CreateMemoryResourceNotification` função na API do Win32.</span><span class="sxs-lookup"><span data-stu-id="fc497-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc497-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc497-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="fc497-106">Membros</span><span class="sxs-lookup"><span data-stu-id="fc497-106">Members</span></span>  
  
|<span data-ttu-id="fc497-107">Membro</span><span class="sxs-lookup"><span data-stu-id="fc497-107">Member</span></span>|<span data-ttu-id="fc497-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc497-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="fc497-109">Muita memória física está disponível.</span><span class="sxs-lookup"><span data-stu-id="fc497-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="fc497-110">Muito pouca memória física está disponível.</span><span class="sxs-lookup"><span data-stu-id="fc497-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="fc497-111">A memória física disponível é neutra.</span><span class="sxs-lookup"><span data-stu-id="fc497-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc497-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc497-112">Remarks</span></span>  
 <span data-ttu-id="fc497-113">Esse valor é passado pelo host para o common language runtime (CLR) pelo uso de uma chamada para o [iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fc497-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc497-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc497-114">Requirements</span></span>  
 <span data-ttu-id="fc497-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc497-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc497-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc497-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc497-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc497-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc497-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc497-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc497-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc497-119">See also</span></span>
- [<span data-ttu-id="fc497-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="fc497-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
