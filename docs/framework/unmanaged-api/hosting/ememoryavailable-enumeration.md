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
ms.openlocfilehash: aec3c5f140df7eab10ea2bfa33634a4d853adcb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134296"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="41c1b-102">Enumeração EMemoryAvailable</span><span class="sxs-lookup"><span data-stu-id="41c1b-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="41c1b-103">Contém valores que indicam a quantidade de memória física livre no computador.</span><span class="sxs-lookup"><span data-stu-id="41c1b-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="41c1b-104">Esses valores são mapeados logicamente para os eventos de memória alta e baixa retornados da função `CreateMemoryResourceNotification` na API do Windows.</span><span class="sxs-lookup"><span data-stu-id="41c1b-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c1b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41c1b-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="41c1b-106">Membros</span><span class="sxs-lookup"><span data-stu-id="41c1b-106">Members</span></span>  
  
|<span data-ttu-id="41c1b-107">Membro</span><span class="sxs-lookup"><span data-stu-id="41c1b-107">Member</span></span>|<span data-ttu-id="41c1b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="41c1b-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="41c1b-109">Há muita memória física disponível.</span><span class="sxs-lookup"><span data-stu-id="41c1b-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="41c1b-110">Há pouca memória física disponível.</span><span class="sxs-lookup"><span data-stu-id="41c1b-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="41c1b-111">A memória física disponível é neutra.</span><span class="sxs-lookup"><span data-stu-id="41c1b-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c1b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="41c1b-112">Remarks</span></span>  
 <span data-ttu-id="41c1b-113">Esse valor é passado pelo host para o Common Language Runtime (CLR) usando uma chamada para o método [ICLRMemoryNotificationCallback:: OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="41c1b-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c1b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41c1b-114">Requirements</span></span>  
 <span data-ttu-id="41c1b-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c1b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c1b-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41c1b-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41c1b-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41c1b-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41c1b-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c1b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c1b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41c1b-119">See also</span></span>

- [<span data-ttu-id="41c1b-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="41c1b-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
