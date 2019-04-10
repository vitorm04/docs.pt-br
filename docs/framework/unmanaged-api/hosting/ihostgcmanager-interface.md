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
ms.openlocfilehash: 238b054d240437df64a83a9c4daad34d4bd5d36a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228869"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="f8709-102">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="f8709-102">IHostGCManager Interface</span></span>
<span data-ttu-id="f8709-103">Fornece métodos que notificar o host de eventos no mecanismo de coleta de lixo implementado pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f8709-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="f8709-104">Membros</span><span class="sxs-lookup"><span data-stu-id="f8709-104">Members</span></span>  
  
|<span data-ttu-id="f8709-105">Membro</span><span class="sxs-lookup"><span data-stu-id="f8709-105">Member</span></span>|<span data-ttu-id="f8709-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8709-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8709-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="f8709-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="f8709-108">Notifica o host que o CLR está continuando a execução de tarefas em threads que tinham sido suspensos para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f8709-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="f8709-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="f8709-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="f8709-110">Notifica o host que o CLR é suspendendo a execução de tarefas para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f8709-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="f8709-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="f8709-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="f8709-112">Notifica o host que o thread do qual a chamada de método foi feita está prestes a bloquear uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f8709-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8709-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8709-113">Requirements</span></span>  
 <span data-ttu-id="f8709-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8709-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8709-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8709-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8709-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f8709-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f8709-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f8709-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f8709-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8709-118">See also</span></span>

- [<span data-ttu-id="f8709-119">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f8709-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f8709-120">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f8709-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f8709-121">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f8709-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f8709-122">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f8709-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f8709-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="f8709-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
