---
title: Método IHostManualEvent::Reset
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 464093291648d7c5c1f2001fbaef85fcd5d592de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136797"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="183da-102">Método IHostManualEvent::Reset</span><span class="sxs-lookup"><span data-stu-id="183da-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="183da-103">Redefine a instância de [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) atual para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="183da-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="183da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="183da-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="183da-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="183da-105">Return Value</span></span>  
  
|<span data-ttu-id="183da-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="183da-106">HRESULT</span></span>|<span data-ttu-id="183da-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="183da-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="183da-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="183da-108">S_OK</span></span>|<span data-ttu-id="183da-109">`Reset` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="183da-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="183da-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="183da-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="183da-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="183da-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="183da-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="183da-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="183da-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="183da-113">The call timed out.</span></span>|  
|<span data-ttu-id="183da-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="183da-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="183da-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="183da-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="183da-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="183da-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="183da-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="183da-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="183da-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="183da-118">E_FAIL</span></span>|<span data-ttu-id="183da-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="183da-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="183da-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="183da-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="183da-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="183da-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="183da-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="183da-122">Requirements</span></span>  
 <span data-ttu-id="183da-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="183da-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="183da-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="183da-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="183da-125">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="183da-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="183da-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="183da-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183da-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="183da-127">See also</span></span>

- [<span data-ttu-id="183da-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="183da-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="183da-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="183da-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="183da-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="183da-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="183da-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="183da-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="183da-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="183da-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
