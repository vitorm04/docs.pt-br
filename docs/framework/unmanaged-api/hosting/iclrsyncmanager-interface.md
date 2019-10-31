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
ms.openlocfilehash: 3593e4d68058a1820f575c92ff9571d43560316a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133926"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="56976-102">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="56976-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="56976-103">Define métodos que permitem ao host obter informações sobre as tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.</span><span class="sxs-lookup"><span data-stu-id="56976-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56976-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="56976-104">Methods</span></span>  
  
|<span data-ttu-id="56976-105">Método</span><span class="sxs-lookup"><span data-stu-id="56976-105">Method</span></span>|<span data-ttu-id="56976-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="56976-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56976-107">Método CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="56976-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="56976-108">Solicita que o Common Language Runtime (CLR) crie um iterador para o host usar para determinar o conjunto de tarefas que estão aguardando um bloqueio do gravador de leitor.</span><span class="sxs-lookup"><span data-stu-id="56976-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="56976-109">Método DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="56976-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="56976-110">Solicita que o CLR destrua um iterador que foi criado por uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="56976-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="56976-111">Método GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="56976-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="56976-112">Obtém a tarefa que possui o monitor especificado.</span><span class="sxs-lookup"><span data-stu-id="56976-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="56976-113">Método GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="56976-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="56976-114">Obtém a próxima tarefa que está aguardando o bloqueio do gravador de leitor atual.</span><span class="sxs-lookup"><span data-stu-id="56976-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56976-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56976-115">Requirements</span></span>  
 <span data-ttu-id="56976-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56976-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56976-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="56976-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56976-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="56976-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56976-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56976-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56976-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56976-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="56976-121">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="56976-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="56976-122">[Threads gerenciados e não gerenciados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="56976-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="56976-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="56976-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
