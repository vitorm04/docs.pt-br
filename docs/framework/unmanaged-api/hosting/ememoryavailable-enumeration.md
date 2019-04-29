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
ms.openlocfilehash: d98a0c1c3187b81c44fae6eee91d975169a40045
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627938"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="f5a6e-102">Enumeração EMemoryAvailable</span><span class="sxs-lookup"><span data-stu-id="f5a6e-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="f5a6e-103">Contém valores que indicam a quantidade de memória física livre no computador.</span><span class="sxs-lookup"><span data-stu-id="f5a6e-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="f5a6e-104">Esses valores são mapeados logicamente para os eventos de alta e baixa memória retornado do `CreateMemoryResourceNotification` função na API do Windows.</span><span class="sxs-lookup"><span data-stu-id="f5a6e-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5a6e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5a6e-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="f5a6e-106">Membros</span><span class="sxs-lookup"><span data-stu-id="f5a6e-106">Members</span></span>  
  
|<span data-ttu-id="f5a6e-107">Membro</span><span class="sxs-lookup"><span data-stu-id="f5a6e-107">Member</span></span>|<span data-ttu-id="f5a6e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5a6e-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="f5a6e-109">Muita memória física está disponível.</span><span class="sxs-lookup"><span data-stu-id="f5a6e-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="f5a6e-110">Muito pouca memória física está disponível.</span><span class="sxs-lookup"><span data-stu-id="f5a6e-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="f5a6e-111">A memória física disponível é neutra.</span><span class="sxs-lookup"><span data-stu-id="f5a6e-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5a6e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5a6e-112">Remarks</span></span>  
 <span data-ttu-id="f5a6e-113">Esse valor é passado pelo host para o common language runtime (CLR) pelo uso de uma chamada para o [iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f5a6e-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5a6e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5a6e-114">Requirements</span></span>  
 <span data-ttu-id="f5a6e-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5a6e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5a6e-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5a6e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5a6e-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5a6e-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5a6e-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5a6e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a6e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5a6e-119">See also</span></span>

- [<span data-ttu-id="f5a6e-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="f5a6e-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
