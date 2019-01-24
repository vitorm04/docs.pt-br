---
title: Método IHostTaskManager::BeginDelayAbort
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61aa68aff5c55586b9de227a72746b3c02234043
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727424"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="f98cf-102">Método IHostTaskManager::BeginDelayAbort</span><span class="sxs-lookup"><span data-stu-id="f98cf-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="f98cf-103">Notifica o host que o código gerenciado está inserindo um período em que a tarefa atual não deve ser anulada.</span><span class="sxs-lookup"><span data-stu-id="f98cf-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f98cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f98cf-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f98cf-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f98cf-105">Return Value</span></span>  
  
|<span data-ttu-id="f98cf-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f98cf-106">HRESULT</span></span>|<span data-ttu-id="f98cf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f98cf-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f98cf-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f98cf-108">S_OK</span></span>|<span data-ttu-id="f98cf-109">`BeginDelayAbort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f98cf-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="f98cf-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f98cf-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f98cf-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f98cf-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f98cf-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f98cf-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f98cf-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f98cf-113">The call timed out.</span></span>|  
|<span data-ttu-id="f98cf-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f98cf-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f98cf-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f98cf-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f98cf-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f98cf-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f98cf-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="f98cf-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f98cf-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f98cf-118">E_FAIL</span></span>|<span data-ttu-id="f98cf-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f98cf-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f98cf-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f98cf-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f98cf-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f98cf-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f98cf-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="f98cf-122">E_UNEXPECTED</span></span>|<span data-ttu-id="f98cf-123">`BeginDelayAbort` já foi chamado, mas a chamada correspondente para [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) ainda não foram recebidos.</span><span class="sxs-lookup"><span data-stu-id="f98cf-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f98cf-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f98cf-124">Remarks</span></span>  
 <span data-ttu-id="f98cf-125">O host não deve cancelar a tarefa atual até que `EndDelayAbort` é chamado.</span><span class="sxs-lookup"><span data-stu-id="f98cf-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="f98cf-126">Se outra chamada para `BeginDelayAbort` é feita sem uma chamada intermediária para `EndDelayAbort`, o host deve retornam E_UNEXPECTED de `BeginDelayAbort`e deve executar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="f98cf-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f98cf-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f98cf-127">Requirements</span></span>  
 <span data-ttu-id="f98cf-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f98cf-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f98cf-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f98cf-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f98cf-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f98cf-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f98cf-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f98cf-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f98cf-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f98cf-132">See also</span></span>
- [<span data-ttu-id="f98cf-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f98cf-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f98cf-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f98cf-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f98cf-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f98cf-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f98cf-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f98cf-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
