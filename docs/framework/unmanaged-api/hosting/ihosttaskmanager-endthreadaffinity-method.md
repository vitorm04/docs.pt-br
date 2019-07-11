---
title: Método IHostTaskManager::EndThreadAffinity
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b50e08e6fe0db7d16c87d9acccf77e2b15094039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749639"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="bae19-102">Método IHostTaskManager::EndThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="bae19-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="bae19-103">Notifica o host que o código gerenciado está saindo do período em que a tarefa atual não deve ser movida para outro thread do sistema operacional, seguindo uma chamada anterior para [ihosttaskmanager:: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="bae19-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bae19-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bae19-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bae19-105">Return Value</span></span>  
  
|<span data-ttu-id="bae19-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bae19-106">HRESULT</span></span>|<span data-ttu-id="bae19-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bae19-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bae19-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bae19-108">S_OK</span></span>|<span data-ttu-id="bae19-109">`EndThreadAffinity` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bae19-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="bae19-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bae19-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bae19-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bae19-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bae19-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bae19-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bae19-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bae19-113">The call timed out.</span></span>|  
|<span data-ttu-id="bae19-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bae19-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bae19-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bae19-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bae19-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bae19-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bae19-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="bae19-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bae19-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bae19-118">E_FAIL</span></span>|<span data-ttu-id="bae19-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bae19-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bae19-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bae19-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bae19-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bae19-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bae19-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="bae19-122">E_UNEXPECTED</span></span>|<span data-ttu-id="bae19-123">`EndThreadAffinity` foi chamado sem uma chamada anterior correspondente ao `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="bae19-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bae19-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="bae19-124">Remarks</span></span>  
 <span data-ttu-id="bae19-125">O CLR faz uma chamada correspondente para `BeginThreadAffinity` na tarefa atual antes de chamar `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="bae19-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="bae19-126">Na ausência de tal chamada correspondente, a implementação do host do [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) deve retornam E_UNEXPECTED e nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="bae19-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bae19-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bae19-127">Requirements</span></span>  
 <span data-ttu-id="bae19-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bae19-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bae19-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bae19-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bae19-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bae19-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bae19-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bae19-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae19-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bae19-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="bae19-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="bae19-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bae19-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="bae19-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bae19-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="bae19-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bae19-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="bae19-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
