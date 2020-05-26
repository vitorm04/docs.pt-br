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
ms.openlocfilehash: a24939ac0b0808546ef3615fae4909c6c3cf8a2e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804990"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="5ca2d-102">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="5ca2d-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="5ca2d-103">Fornece uma representação da implementação do host de um evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="5ca2d-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ca2d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5ca2d-104">Methods</span></span>  
  
|<span data-ttu-id="5ca2d-105">Método</span><span class="sxs-lookup"><span data-stu-id="5ca2d-105">Method</span></span>|<span data-ttu-id="5ca2d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ca2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ca2d-107">Método Set</span><span class="sxs-lookup"><span data-stu-id="5ca2d-107">Set Method</span></span>](ihostautoevent-set-method.md)|<span data-ttu-id="5ca2d-108">Define a `IHostAutoEvent` instância atual para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="5ca2d-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="5ca2d-109">Método Wait</span><span class="sxs-lookup"><span data-stu-id="5ca2d-109">Wait Method</span></span>](ihostautoevent-wait-method.md)|<span data-ttu-id="5ca2d-110">Faz com que a `IHostAutoEvent` instância atual aguarde até que o evento seja propriedade ou um período de tempo especificado decorre.</span><span class="sxs-lookup"><span data-stu-id="5ca2d-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ca2d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ca2d-111">Requirements</span></span>  
 <span data-ttu-id="5ca2d-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ca2d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ca2d-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ca2d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ca2d-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ca2d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ca2d-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ca2d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca2d-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ca2d-116">See also</span></span>

- [<span data-ttu-id="5ca2d-117">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="5ca2d-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="5ca2d-118">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="5ca2d-118">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="5ca2d-119">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="5ca2d-119">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="5ca2d-120">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5ca2d-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
