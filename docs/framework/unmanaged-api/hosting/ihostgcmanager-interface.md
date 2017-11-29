---
title: Interface IHostGCManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager
helpviewer_keywords: IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0927b236af094b964261a9b2a49a33d1ea2b9391
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="99f39-102">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="99f39-102">IHostGCManager Interface</span></span>
<span data-ttu-id="99f39-103">Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="99f39-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="99f39-104">Membros</span><span class="sxs-lookup"><span data-stu-id="99f39-104">Members</span></span>  
  
|<span data-ttu-id="99f39-105">Membro</span><span class="sxs-lookup"><span data-stu-id="99f39-105">Member</span></span>|<span data-ttu-id="99f39-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="99f39-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99f39-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="99f39-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="99f39-108">Notifica o host que o CLR está continuando a execução de tarefas em threads que foi suspenso para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="99f39-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="99f39-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="99f39-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="99f39-110">Notifica o host que o CLR é suspender a execução de tarefas para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="99f39-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="99f39-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="99f39-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="99f39-112">Notifica o host que o thread do qual foi feita a chamada do método está prestes a bloquear uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="99f39-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99f39-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99f39-113">Requirements</span></span>  
 <span data-ttu-id="99f39-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99f39-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99f39-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99f39-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99f39-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="99f39-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99f39-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99f39-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f39-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99f39-118">See Also</span></span>  
 [<span data-ttu-id="99f39-119">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="99f39-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="99f39-120">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="99f39-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="99f39-121">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="99f39-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="99f39-122">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="99f39-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="99f39-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="99f39-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
