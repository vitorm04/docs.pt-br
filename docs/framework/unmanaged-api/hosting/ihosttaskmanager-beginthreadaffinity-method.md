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
ms.openlocfilehash: 7c157cf27d2fe86288024a6c35e6dcbea3c46347
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133114"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="26c38-102">Método IHostTaskManager::BeginThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="26c38-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="26c38-103">Notifica o host de que o código gerenciado está entrando em um período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="26c38-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26c38-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="26c38-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="26c38-105">Return Value</span></span>  
  
|<span data-ttu-id="26c38-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26c38-106">HRESULT</span></span>|<span data-ttu-id="26c38-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="26c38-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26c38-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="26c38-108">S_OK</span></span>|<span data-ttu-id="26c38-109">`BeginThreadAffinity` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="26c38-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="26c38-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26c38-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26c38-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="26c38-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26c38-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26c38-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26c38-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="26c38-113">The call timed out.</span></span>|  
|<span data-ttu-id="26c38-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26c38-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26c38-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="26c38-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26c38-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26c38-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26c38-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="26c38-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26c38-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26c38-118">E_FAIL</span></span>|<span data-ttu-id="26c38-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="26c38-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26c38-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="26c38-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26c38-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="26c38-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26c38-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="26c38-122">Remarks</span></span>  
 <span data-ttu-id="26c38-123">O CLR normalmente chama `IHostTaskManager::BeginThreadAffinity` no contexto de uma chamada para <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26c38-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26c38-124">A tarefa atual não deve ser reagendada até que uma chamada correspondente seja feita a [IHostTaskManager:: EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="26c38-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="26c38-125">As tarefas podem ser desativadas, mas quando elas são reativadas, elas devem ser atribuídas ao mesmo thread do sistema operacional do qual foram desativadas. Chamadas aninhadas para `BeginThreadAffinity` não têm efeito, porque a chamada se refere à tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="26c38-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c38-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26c38-126">Requirements</span></span>  
 <span data-ttu-id="26c38-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26c38-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c38-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26c38-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26c38-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26c38-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26c38-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c38-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c38-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26c38-131">See also</span></span>

- [<span data-ttu-id="26c38-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="26c38-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="26c38-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="26c38-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="26c38-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="26c38-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="26c38-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="26c38-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
