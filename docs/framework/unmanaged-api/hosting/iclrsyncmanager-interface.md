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
ms.openlocfilehash: b0b9c0b7d178557806a9ab2893bff2d34dc408ff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557730"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="8e9c4-102">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="8e9c4-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="8e9c4-103">Define métodos que permitem ao host obter informações sobre as tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.</span><span class="sxs-lookup"><span data-stu-id="8e9c4-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e9c4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8e9c4-104">Methods</span></span>  
  
|<span data-ttu-id="8e9c4-105">Método</span><span class="sxs-lookup"><span data-stu-id="8e9c4-105">Method</span></span>|<span data-ttu-id="8e9c4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e9c4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e9c4-107">Método CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="8e9c4-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="8e9c4-108">Solicita que o Common Language Runtime (CLR) crie um iterador para o host usar para determinar o conjunto de tarefas que estão aguardando um bloqueio do gravador de leitor.</span><span class="sxs-lookup"><span data-stu-id="8e9c4-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="8e9c4-109">Método DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="8e9c4-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="8e9c4-110">Solicita que o CLR destrua um iterador criado por uma chamada para `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="8e9c4-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="8e9c4-111">Método GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="8e9c4-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="8e9c4-112">Obtém a tarefa que possui o monitor especificado.</span><span class="sxs-lookup"><span data-stu-id="8e9c4-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="8e9c4-113">Método GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="8e9c4-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="8e9c4-114">Obtém a próxima tarefa que está aguardando o bloqueio do gravador de leitor atual.</span><span class="sxs-lookup"><span data-stu-id="8e9c4-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e9c4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e9c4-115">Requirements</span></span>  
 <span data-ttu-id="8e9c4-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e9c4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e9c4-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8e9c4-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e9c4-118">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e9c4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e9c4-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e9c4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e9c4-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e9c4-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="8e9c4-121">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="8e9c4-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="8e9c4-122">[Threading gerenciado e não gerenciado](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8e9c4-122">[Managed and Unmanaged Threading](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="8e9c4-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8e9c4-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
