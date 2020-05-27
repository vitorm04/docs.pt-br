---
title: Método IHostTaskManager::BeginThreadAffinity
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 90ae790603f0e41a20993ffef88654211a3168d9
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842355"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="6c26c-102">Método IHostTaskManager::BeginThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="6c26c-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="6c26c-103">Notifica o host de que o código gerenciado está entrando em um período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="6c26c-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c26c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c26c-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6c26c-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6c26c-105">Return Value</span></span>  
  
|<span data-ttu-id="6c26c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c26c-106">HRESULT</span></span>|<span data-ttu-id="6c26c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c26c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c26c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c26c-108">S_OK</span></span>|<span data-ttu-id="6c26c-109">`BeginThreadAffinity`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6c26c-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="6c26c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c26c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c26c-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6c26c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c26c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c26c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c26c-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6c26c-113">The call timed out.</span></span>|  
|<span data-ttu-id="6c26c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c26c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c26c-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6c26c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c26c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c26c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c26c-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="6c26c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c26c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c26c-118">E_FAIL</span></span>|<span data-ttu-id="6c26c-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6c26c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c26c-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="6c26c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c26c-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6c26c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c26c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c26c-122">Remarks</span></span>  
 <span data-ttu-id="6c26c-123">Normalmente, o CLR chama `IHostTaskManager::BeginThreadAffinity` o contexto de uma chamada para <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6c26c-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6c26c-124">A tarefa atual não deve ser reagendada até que uma chamada correspondente seja feita a [IHostTaskManager:: EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="6c26c-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="6c26c-125">As tarefas podem ser desativadas, mas quando elas são reativadas, elas devem ser atribuídas ao mesmo thread do sistema operacional do qual foram desativadas. Chamadas aninhadas `BeginThreadAffinity` não têm efeito, pois a chamada se refere à tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="6c26c-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c26c-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c26c-126">Requirements</span></span>  
 <span data-ttu-id="6c26c-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c26c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c26c-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c26c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c26c-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c26c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c26c-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c26c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c26c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c26c-131">See also</span></span>

- [<span data-ttu-id="6c26c-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="6c26c-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6c26c-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="6c26c-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6c26c-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="6c26c-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6c26c-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="6c26c-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
