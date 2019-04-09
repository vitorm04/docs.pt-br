---
title: Método IHostTaskManager::EndDelayAbort
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d12e5cab41f016ddee78089dc1df1f5c942ecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194435"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="43e32-102">Método IHostTaskManager::EndDelayAbort</span><span class="sxs-lookup"><span data-stu-id="43e32-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="43e32-103">Notifica o host que o código gerenciado está saindo do período em que a tarefa atual não deve ser interrompida, após uma chamada anterior para [ihosttaskmanager:: Begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="43e32-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43e32-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43e32-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="43e32-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="43e32-105">Return Value</span></span>  
  
|<span data-ttu-id="43e32-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43e32-106">HRESULT</span></span>|<span data-ttu-id="43e32-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="43e32-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43e32-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="43e32-108">S_OK</span></span>|`EndDelayAbort` <span data-ttu-id="43e32-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="43e32-109">returned successfully.</span></span>|  
|<span data-ttu-id="43e32-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43e32-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43e32-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="43e32-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43e32-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43e32-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43e32-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="43e32-113">The call timed out.</span></span>|  
|<span data-ttu-id="43e32-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43e32-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43e32-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="43e32-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43e32-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43e32-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43e32-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="43e32-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43e32-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43e32-118">E_FAIL</span></span>|<span data-ttu-id="43e32-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="43e32-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43e32-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="43e32-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43e32-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="43e32-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="43e32-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="43e32-122">E_UNEXPECTED</span></span>|`EndDelayAbort` <span data-ttu-id="43e32-123">foi chamado sem uma chamada correspondente para `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="43e32-123">was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43e32-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="43e32-124">Remarks</span></span>  
 <span data-ttu-id="43e32-125">O CLR faz uma chamada correspondente para `BeginDelayAbort` na tarefa atual antes de chamar `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="43e32-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="43e32-126">Na ausência de tal chamada correspondente, a implementação do host do [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) deve retornar E_UNEXPECTED de `EndDelayAbort`e deve executar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="43e32-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43e32-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43e32-127">Requirements</span></span>  
 <span data-ttu-id="43e32-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43e32-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43e32-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43e32-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43e32-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="43e32-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="43e32-131">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="43e32-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43e32-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43e32-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="43e32-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="43e32-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="43e32-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="43e32-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="43e32-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="43e32-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="43e32-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="43e32-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
