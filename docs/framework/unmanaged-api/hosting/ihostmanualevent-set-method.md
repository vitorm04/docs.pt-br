---
title: Método IHostManualEvent::Set
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3756ed3bc7863411849b9d733da816e567a86628
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767309"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="e0be0-102">Método IHostManualEvent::Set</span><span class="sxs-lookup"><span data-stu-id="e0be0-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="e0be0-103">Define o atual [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instância para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="e0be0-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0be0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0be0-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e0be0-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e0be0-105">Return Value</span></span>  
  
|<span data-ttu-id="e0be0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0be0-106">HRESULT</span></span>|<span data-ttu-id="e0be0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0be0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0be0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0be0-108">S_OK</span></span>|<span data-ttu-id="e0be0-109">`Set` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e0be0-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="e0be0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0be0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0be0-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e0be0-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0be0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0be0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0be0-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e0be0-113">The call timed out.</span></span>|  
|<span data-ttu-id="e0be0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0be0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0be0-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e0be0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0be0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0be0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0be0-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e0be0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0be0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0be0-118">E_FAIL</span></span>|<span data-ttu-id="e0be0-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e0be0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0be0-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e0be0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0be0-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0be0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0be0-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0be0-122">Requirements</span></span>  
 <span data-ttu-id="e0be0-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0be0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0be0-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0be0-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0be0-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e0be0-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0be0-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0be0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0be0-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0be0-127">See also</span></span>

- [<span data-ttu-id="e0be0-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="e0be0-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e0be0-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="e0be0-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e0be0-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="e0be0-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e0be0-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="e0be0-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="e0be0-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="e0be0-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
