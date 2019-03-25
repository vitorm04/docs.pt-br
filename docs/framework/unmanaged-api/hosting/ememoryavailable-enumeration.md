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
ms.openlocfilehash: 55463985a7ac93bf0ec3cda92f91f8a326f92406
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410557"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="3677d-102">Enumeração EMemoryAvailable</span><span class="sxs-lookup"><span data-stu-id="3677d-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="3677d-103">Contém valores que indicam a quantidade de memória física livre no computador.</span><span class="sxs-lookup"><span data-stu-id="3677d-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="3677d-104">Esses valores são mapeados logicamente para os eventos de alta e baixa memória retornado do `CreateMemoryResourceNotification` função na API do Windows.</span><span class="sxs-lookup"><span data-stu-id="3677d-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3677d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3677d-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="3677d-106">Membros</span><span class="sxs-lookup"><span data-stu-id="3677d-106">Members</span></span>  
  
|<span data-ttu-id="3677d-107">Membro</span><span class="sxs-lookup"><span data-stu-id="3677d-107">Member</span></span>|<span data-ttu-id="3677d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="3677d-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="3677d-109">Muita memória física está disponível.</span><span class="sxs-lookup"><span data-stu-id="3677d-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="3677d-110">Muito pouca memória física está disponível.</span><span class="sxs-lookup"><span data-stu-id="3677d-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="3677d-111">A memória física disponível é neutra.</span><span class="sxs-lookup"><span data-stu-id="3677d-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3677d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="3677d-112">Remarks</span></span>  
 <span data-ttu-id="3677d-113">Esse valor é passado pelo host para o common language runtime (CLR) pelo uso de uma chamada para o [iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="3677d-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3677d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3677d-114">Requirements</span></span>  
 <span data-ttu-id="3677d-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3677d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3677d-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3677d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3677d-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3677d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3677d-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3677d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3677d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3677d-119">See also</span></span>
- [<span data-ttu-id="3677d-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="3677d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
