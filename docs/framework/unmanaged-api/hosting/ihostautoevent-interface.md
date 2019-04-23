---
title: Interface IHostAutoEvent
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb5fea403f8210ea93d240aa3aabd4325524b987
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080937"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="54b4e-102">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="54b4e-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="54b4e-103">Fornece uma representação da implementação do host de um evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="54b4e-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54b4e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="54b4e-104">Methods</span></span>  
  
|<span data-ttu-id="54b4e-105">Método</span><span class="sxs-lookup"><span data-stu-id="54b4e-105">Method</span></span>|<span data-ttu-id="54b4e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="54b4e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54b4e-107">Método Set</span><span class="sxs-lookup"><span data-stu-id="54b4e-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="54b4e-108">Define o atual `IHostAutoEvent` instância para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="54b4e-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="54b4e-109">Método Wait</span><span class="sxs-lookup"><span data-stu-id="54b4e-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="54b4e-110">Faz com que o atual `IHostAutoEvent` instância aguardar até que o evento é de propriedade ou uma quantidade especificada de tempo passa.</span><span class="sxs-lookup"><span data-stu-id="54b4e-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54b4e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54b4e-111">Requirements</span></span>  
 <span data-ttu-id="54b4e-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54b4e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54b4e-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54b4e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54b4e-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="54b4e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54b4e-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54b4e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54b4e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54b4e-116">See also</span></span>

- [<span data-ttu-id="54b4e-117">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="54b4e-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="54b4e-118">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="54b4e-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="54b4e-119">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="54b4e-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="54b4e-120">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="54b4e-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
