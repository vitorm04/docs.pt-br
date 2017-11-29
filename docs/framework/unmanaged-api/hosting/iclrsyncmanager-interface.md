---
title: Interface ICLRSyncManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e47f02a5a84b909b03c6be4e0a43c7166a1ddc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="77731-102">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="77731-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="77731-103">Define métodos que permitem que o host para obter informações sobre tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.</span><span class="sxs-lookup"><span data-stu-id="77731-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77731-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="77731-104">Methods</span></span>  
  
|<span data-ttu-id="77731-105">Método</span><span class="sxs-lookup"><span data-stu-id="77731-105">Method</span></span>|<span data-ttu-id="77731-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="77731-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77731-107">Método CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="77731-107">CreateRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="77731-108">Solicita que o common language runtime (CLR) criar um iterador para o host a ser usado para determinar o conjunto de tarefas que esperam por um bloqueio de leitor / gravador.</span><span class="sxs-lookup"><span data-stu-id="77731-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="77731-109">Método DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="77731-109">DeleteRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="77731-110">Solicita que o CLR destruir um iterador que foi criado por uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="77731-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="77731-111">Método GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="77731-111">GetMonitorOwner Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="77731-112">Obtém a tarefa que tem o monitor de especificados.</span><span class="sxs-lookup"><span data-stu-id="77731-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="77731-113">Método GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="77731-113">GetRWLockOwnerNext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="77731-114">Obtém a próxima tarefa está aguardando o bloqueio de leitor-gravador atual.</span><span class="sxs-lookup"><span data-stu-id="77731-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77731-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77731-115">Requirements</span></span>  
 <span data-ttu-id="77731-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77731-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77731-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77731-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77731-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="77731-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77731-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77731-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77731-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77731-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="77731-121">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="77731-121">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="77731-122">Threading gerenciado e não gerenciado</span><span class="sxs-lookup"><span data-stu-id="77731-122">Managed and Unmanaged Threading</span></span>](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [<span data-ttu-id="77731-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="77731-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
