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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4eac8abede82915386abc19c4c8389932451df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440370"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="59927-102">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="59927-102">IHostGCManager Interface</span></span>
<span data-ttu-id="59927-103">Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="59927-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="59927-104">Membros</span><span class="sxs-lookup"><span data-stu-id="59927-104">Members</span></span>  
  
|<span data-ttu-id="59927-105">Membro</span><span class="sxs-lookup"><span data-stu-id="59927-105">Member</span></span>|<span data-ttu-id="59927-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="59927-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59927-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="59927-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="59927-108">Notifica o host que o CLR está continuando a execução de tarefas em threads que foi suspenso para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="59927-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="59927-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="59927-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="59927-110">Notifica o host que o CLR é suspender a execução de tarefas para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="59927-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="59927-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="59927-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="59927-112">Notifica o host que o thread do qual foi feita a chamada do método está prestes a bloquear uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="59927-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59927-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59927-113">Requirements</span></span>  
 <span data-ttu-id="59927-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59927-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59927-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="59927-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59927-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="59927-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59927-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59927-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59927-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59927-118">See Also</span></span>  
 [<span data-ttu-id="59927-119">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="59927-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="59927-120">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="59927-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="59927-121">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="59927-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="59927-122">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="59927-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="59927-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="59927-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
