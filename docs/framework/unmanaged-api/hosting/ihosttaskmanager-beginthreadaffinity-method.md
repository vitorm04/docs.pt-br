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
ms.openlocfilehash: 7eb5c7ec85c0adb301fb722155caaed3c14e0e19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137716"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="83534-102">Método IHostTaskManager::BeginThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="83534-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="83534-103">Notifica o host que o código gerenciado está inserindo um período em que a tarefa atual não deve ser movida para outro thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="83534-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83534-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83534-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="83534-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="83534-105">Return Value</span></span>  
  
|<span data-ttu-id="83534-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83534-106">HRESULT</span></span>|<span data-ttu-id="83534-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="83534-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83534-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="83534-108">S_OK</span></span>|`BeginThreadAffinity` <span data-ttu-id="83534-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="83534-109">returned successfully.</span></span>|  
|<span data-ttu-id="83534-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83534-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83534-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="83534-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83534-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83534-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83534-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="83534-113">The call timed out.</span></span>|  
|<span data-ttu-id="83534-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83534-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83534-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="83534-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83534-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83534-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83534-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="83534-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83534-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83534-118">E_FAIL</span></span>|<span data-ttu-id="83534-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="83534-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83534-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="83534-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83534-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83534-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83534-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="83534-122">Remarks</span></span>  
 <span data-ttu-id="83534-123">O CLR chama normalmente `IHostTaskManager::BeginThreadAffinity` no contexto de uma chamada para <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83534-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83534-124">A tarefa atual não deve ser reagendada até que seja feita uma chamada correspondente [ihosttaskmanager:: EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="83534-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="83534-125">Tarefas podem ser desativadas, mas quando eles são alternados novamente, deve ser atribuídos para o mesmo thread do sistema operacional do qual foi desativadas. Aninhadas chamadas para `BeginThreadAffinity` não têm nenhum efeito, porque a chamada se refere à tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="83534-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83534-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83534-126">Requirements</span></span>  
 <span data-ttu-id="83534-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83534-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83534-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83534-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83534-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="83534-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="83534-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="83534-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83534-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83534-131">See also</span></span>

- [<span data-ttu-id="83534-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="83534-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="83534-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="83534-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="83534-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="83534-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="83534-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="83534-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
