---
title: Interface IHostManualEvent
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb09422872a0d9565be286c25ca1b28d1c45e08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501692"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="eebf7-102">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="eebf7-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="eebf7-103">Fornece a implementação do host de uma representação de um evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="eebf7-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eebf7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="eebf7-104">Methods</span></span>  
  
|<span data-ttu-id="eebf7-105">Método</span><span class="sxs-lookup"><span data-stu-id="eebf7-105">Method</span></span>|<span data-ttu-id="eebf7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="eebf7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eebf7-107">Método Reset</span><span class="sxs-lookup"><span data-stu-id="eebf7-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="eebf7-108">Redefine o atual `IHostManualEvent` instância para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="eebf7-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="eebf7-109">Método Set</span><span class="sxs-lookup"><span data-stu-id="eebf7-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="eebf7-110">Define o atual `IHostManualEvent` instância para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="eebf7-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="eebf7-111">Método Wait</span><span class="sxs-lookup"><span data-stu-id="eebf7-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="eebf7-112">Faz com que o atual `IHostManualEvent` instância aguardar até que ele pertence, ou uma quantidade especificada de tempo passa.</span><span class="sxs-lookup"><span data-stu-id="eebf7-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eebf7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eebf7-113">Requirements</span></span>  
 <span data-ttu-id="eebf7-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eebf7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eebf7-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eebf7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eebf7-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="eebf7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eebf7-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eebf7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebf7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eebf7-118">See also</span></span>
- [<span data-ttu-id="eebf7-119">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="eebf7-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="eebf7-120">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="eebf7-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="eebf7-121">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="eebf7-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="eebf7-122">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="eebf7-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="eebf7-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="eebf7-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
