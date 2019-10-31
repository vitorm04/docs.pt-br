---
title: Interface IHostGCManager
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: 6f7158bcac7ad22647104e2041da959285d2be8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130490"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="f4afc-102">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="f4afc-102">IHostGCManager Interface</span></span>
<span data-ttu-id="f4afc-103">Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f4afc-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="f4afc-104">Membros</span><span class="sxs-lookup"><span data-stu-id="f4afc-104">Members</span></span>  
  
|<span data-ttu-id="f4afc-105">Membro</span><span class="sxs-lookup"><span data-stu-id="f4afc-105">Member</span></span>|<span data-ttu-id="f4afc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4afc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4afc-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="f4afc-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="f4afc-108">Notifica o host de que o CLR está retomando a execução de tarefas em threads que foram suspensos para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f4afc-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="f4afc-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="f4afc-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="f4afc-110">Notifica o host de que o CLR está suspendendo a execução de tarefas, para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f4afc-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="f4afc-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="f4afc-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="f4afc-112">Notifica o host de que o thread do qual a chamada de método foi feita está prestes a ser bloqueado para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f4afc-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4afc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4afc-113">Requirements</span></span>  
 <span data-ttu-id="f4afc-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4afc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4afc-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f4afc-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4afc-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f4afc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4afc-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4afc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4afc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4afc-118">See also</span></span>

- [<span data-ttu-id="f4afc-119">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f4afc-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f4afc-120">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f4afc-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f4afc-121">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f4afc-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f4afc-122">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f4afc-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f4afc-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f4afc-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
