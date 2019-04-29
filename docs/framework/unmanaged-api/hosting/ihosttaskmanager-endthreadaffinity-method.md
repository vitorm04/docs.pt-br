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
ms.openlocfilehash: 3f94f365aa8c9221c64e9611deab3597e06ed862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789416"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="4c0d2-102">Método IHostTaskManager::EndThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="4c0d2-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="4c0d2-103">Notifica o host que o código gerenciado está saindo do período em que a tarefa atual não deve ser movida para outro thread do sistema operacional, seguindo uma chamada anterior para [ihosttaskmanager:: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="4c0d2-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c0d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c0d2-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4c0d2-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4c0d2-105">Return Value</span></span>  
  
|<span data-ttu-id="4c0d2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c0d2-106">HRESULT</span></span>|<span data-ttu-id="4c0d2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c0d2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c0d2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c0d2-108">S_OK</span></span>|<span data-ttu-id="4c0d2-109">`EndThreadAffinity` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="4c0d2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c0d2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c0d2-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c0d2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c0d2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c0d2-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-113">The call timed out.</span></span>|  
|<span data-ttu-id="4c0d2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c0d2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c0d2-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c0d2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c0d2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c0d2-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c0d2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c0d2-118">E_FAIL</span></span>|<span data-ttu-id="4c0d2-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c0d2-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c0d2-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4c0d2-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="4c0d2-122">E_UNEXPECTED</span></span>|<span data-ttu-id="4c0d2-123">`EndThreadAffinity` foi chamado sem uma chamada anterior correspondente ao `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c0d2-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c0d2-124">Remarks</span></span>  
 <span data-ttu-id="4c0d2-125">O CLR faz uma chamada correspondente para `BeginThreadAffinity` na tarefa atual antes de chamar `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="4c0d2-126">Na ausência de tal chamada correspondente, a implementação do host do [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) deve retornam E_UNEXPECTED e nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="4c0d2-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0d2-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c0d2-127">Requirements</span></span>  
 <span data-ttu-id="4c0d2-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c0d2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0d2-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c0d2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c0d2-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4c0d2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c0d2-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c0d2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0d2-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c0d2-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="4c0d2-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="4c0d2-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4c0d2-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="4c0d2-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4c0d2-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="4c0d2-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4c0d2-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="4c0d2-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
