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
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804848"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="7303f-102">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="7303f-102">IHostGCManager Interface</span></span>
<span data-ttu-id="7303f-103">Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7303f-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="7303f-104">Membros</span><span class="sxs-lookup"><span data-stu-id="7303f-104">Members</span></span>  
  
|<span data-ttu-id="7303f-105">Membro</span><span class="sxs-lookup"><span data-stu-id="7303f-105">Member</span></span>|<span data-ttu-id="7303f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7303f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7303f-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="7303f-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="7303f-108">Notifica o host de que o CLR está retomando a execução de tarefas em threads que foram suspensos para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7303f-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="7303f-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="7303f-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="7303f-110">Notifica o host de que o CLR está suspendendo a execução de tarefas, para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7303f-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="7303f-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="7303f-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="7303f-112">Notifica o host de que o thread do qual a chamada de método foi feita está prestes a ser bloqueado para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7303f-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7303f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7303f-113">Requirements</span></span>  
 <span data-ttu-id="7303f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7303f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7303f-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7303f-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7303f-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7303f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7303f-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7303f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7303f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="7303f-118">See also</span></span>

- [<span data-ttu-id="7303f-119">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7303f-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7303f-120">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7303f-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7303f-121">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7303f-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7303f-122">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7303f-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="7303f-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7303f-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
