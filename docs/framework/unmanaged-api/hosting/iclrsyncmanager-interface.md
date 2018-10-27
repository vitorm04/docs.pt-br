---
title: Interface ICLRSyncManager
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ede896cdb93217fcfba9d66ed7102bcc1ba762e9
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041824"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="97b87-102">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="97b87-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="97b87-103">Define métodos que permitem que o host para obter informações sobre tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.</span><span class="sxs-lookup"><span data-stu-id="97b87-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97b87-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="97b87-104">Methods</span></span>  
  
|<span data-ttu-id="97b87-105">Método</span><span class="sxs-lookup"><span data-stu-id="97b87-105">Method</span></span>|<span data-ttu-id="97b87-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="97b87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97b87-107">Método CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="97b87-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="97b87-108">Solicita que o common language runtime (CLR) cria um iterador para o host a usar para determinar o conjunto de tarefas aguardando um bloqueio de leitor-gravador.</span><span class="sxs-lookup"><span data-stu-id="97b87-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="97b87-109">Método DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="97b87-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="97b87-110">Solicita que o CLR destrua um iterador que foi criado por uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="97b87-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="97b87-111">Método GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="97b87-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="97b87-112">Obtém a tarefa que possui o monitor especificado.</span><span class="sxs-lookup"><span data-stu-id="97b87-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="97b87-113">Método GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="97b87-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="97b87-114">Obtém a próxima tarefa está aguardando o bloqueio de leitor-gravador atual.</span><span class="sxs-lookup"><span data-stu-id="97b87-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97b87-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97b87-115">Requirements</span></span>  
 <span data-ttu-id="97b87-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97b87-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97b87-117">**Cabeçalho:** mscoree. H</span><span class="sxs-lookup"><span data-stu-id="97b87-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97b87-118">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="97b87-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97b87-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97b87-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b87-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97b87-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="97b87-121">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="97b87-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="97b87-122">[Threading gerenciado e não gerenciado](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="97b87-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>  
 [<span data-ttu-id="97b87-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="97b87-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
