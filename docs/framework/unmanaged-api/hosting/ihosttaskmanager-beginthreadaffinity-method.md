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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a94797e6279a1f1d419b977c22d73ca41bbafc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443366"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="80a6d-102">Método IHostTaskManager::BeginThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="80a6d-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="80a6d-103">Notifica o host que o código gerenciado está inserindo um período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="80a6d-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80a6d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80a6d-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="80a6d-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="80a6d-105">Return Value</span></span>  
  
|<span data-ttu-id="80a6d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80a6d-106">HRESULT</span></span>|<span data-ttu-id="80a6d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="80a6d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80a6d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="80a6d-108">S_OK</span></span>|<span data-ttu-id="80a6d-109">`BeginThreadAffinity` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="80a6d-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="80a6d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80a6d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80a6d-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="80a6d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80a6d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80a6d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80a6d-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="80a6d-113">The call timed out.</span></span>|  
|<span data-ttu-id="80a6d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80a6d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80a6d-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="80a6d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80a6d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80a6d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80a6d-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="80a6d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80a6d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80a6d-118">E_FAIL</span></span>|<span data-ttu-id="80a6d-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="80a6d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80a6d-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="80a6d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80a6d-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="80a6d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80a6d-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="80a6d-122">Remarks</span></span>  
 <span data-ttu-id="80a6d-123">O CLR chama normalmente `IHostTaskManager::BeginThreadAffinity` no contexto de uma chamada para <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80a6d-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80a6d-124">A tarefa atual não deve ser reagendada até que é feita uma chamada correspondente para [EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="80a6d-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="80a6d-125">Tarefas podem ser alternadas, mas quando eles são alternados novamente, eles devem ser atribuídos a mesmo thread do sistema operacional do qual eles foram alternados. Aninhadas chamadas para `BeginThreadAffinity` não têm nenhum efeito, porque se refere a chamada para a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="80a6d-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80a6d-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80a6d-126">Requirements</span></span>  
 <span data-ttu-id="80a6d-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80a6d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80a6d-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80a6d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80a6d-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="80a6d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80a6d-130">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80a6d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a6d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80a6d-131">See Also</span></span>  
 [<span data-ttu-id="80a6d-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="80a6d-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="80a6d-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="80a6d-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="80a6d-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="80a6d-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="80a6d-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="80a6d-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
