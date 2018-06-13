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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2dcc342c218b3d6999d777e2658424c92f7e07a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438783"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="4a5b5-102">Método IHostManualEvent::Reset</span><span class="sxs-lookup"><span data-stu-id="4a5b5-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="4a5b5-103">Redefine o atual [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instância para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a5b5-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4a5b5-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4a5b5-105">Return Value</span></span>  
  
|<span data-ttu-id="4a5b5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a5b5-106">HRESULT</span></span>|<span data-ttu-id="4a5b5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a5b5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a5b5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a5b5-108">S_OK</span></span>|<span data-ttu-id="4a5b5-109">`Reset` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="4a5b5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a5b5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a5b5-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a5b5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a5b5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a5b5-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-113">The call timed out.</span></span>|  
|<span data-ttu-id="4a5b5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a5b5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a5b5-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a5b5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a5b5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a5b5-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a5b5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a5b5-118">E_FAIL</span></span>|<span data-ttu-id="4a5b5-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a5b5-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a5b5-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a5b5-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a5b5-122">Requirements</span></span>  
 <span data-ttu-id="4a5b5-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a5b5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a5b5-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a5b5-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a5b5-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4a5b5-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a5b5-126">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a5b5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5b5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a5b5-127">See Also</span></span>  
 [<span data-ttu-id="4a5b5-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="4a5b5-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4a5b5-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="4a5b5-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="4a5b5-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="4a5b5-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="4a5b5-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="4a5b5-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="4a5b5-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="4a5b5-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
