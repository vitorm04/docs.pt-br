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
ms.openlocfilehash: 1114fc744ac1811585f2c5a94858b75eda00815c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136766"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="99f8a-102">Método IHostManualEvent::Set</span><span class="sxs-lookup"><span data-stu-id="99f8a-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="99f8a-103">Define a instância de [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) atual para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="99f8a-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99f8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99f8a-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="99f8a-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="99f8a-105">Return Value</span></span>  
  
|<span data-ttu-id="99f8a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99f8a-106">HRESULT</span></span>|<span data-ttu-id="99f8a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="99f8a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99f8a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="99f8a-108">S_OK</span></span>|<span data-ttu-id="99f8a-109">`Set` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="99f8a-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="99f8a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99f8a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99f8a-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="99f8a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99f8a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99f8a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99f8a-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="99f8a-113">The call timed out.</span></span>|  
|<span data-ttu-id="99f8a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99f8a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99f8a-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="99f8a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99f8a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99f8a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99f8a-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="99f8a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99f8a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99f8a-118">E_FAIL</span></span>|<span data-ttu-id="99f8a-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="99f8a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99f8a-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="99f8a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99f8a-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="99f8a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99f8a-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99f8a-122">Requirements</span></span>  
 <span data-ttu-id="99f8a-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99f8a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99f8a-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99f8a-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99f8a-125">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99f8a-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99f8a-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99f8a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f8a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99f8a-127">See also</span></span>

- [<span data-ttu-id="99f8a-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="99f8a-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="99f8a-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="99f8a-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="99f8a-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="99f8a-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="99f8a-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="99f8a-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="99f8a-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="99f8a-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
