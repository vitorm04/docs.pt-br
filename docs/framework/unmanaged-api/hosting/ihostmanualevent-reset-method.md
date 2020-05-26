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
ms.openlocfilehash: 049a0ae6d860c7c431d08af8ba4539656b8e5592
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804581"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="e299b-102">Método IHostManualEvent::Reset</span><span class="sxs-lookup"><span data-stu-id="e299b-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="e299b-103">Redefine a instância de [IHostManualEvent](ihostmanualevent-interface.md) atual para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="e299b-103">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e299b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e299b-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e299b-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e299b-105">Return Value</span></span>  
  
|<span data-ttu-id="e299b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e299b-106">HRESULT</span></span>|<span data-ttu-id="e299b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e299b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e299b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e299b-108">S_OK</span></span>|<span data-ttu-id="e299b-109">`Reset`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e299b-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="e299b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e299b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e299b-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e299b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e299b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e299b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e299b-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e299b-113">The call timed out.</span></span>|  
|<span data-ttu-id="e299b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e299b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e299b-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e299b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e299b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e299b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e299b-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e299b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e299b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e299b-118">E_FAIL</span></span>|<span data-ttu-id="e299b-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e299b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e299b-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e299b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e299b-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e299b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e299b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e299b-122">Requirements</span></span>  
 <span data-ttu-id="e299b-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e299b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e299b-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e299b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e299b-125">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e299b-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e299b-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e299b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e299b-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="e299b-127">See also</span></span>

- [<span data-ttu-id="e299b-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="e299b-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e299b-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="e299b-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="e299b-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="e299b-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="e299b-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="e299b-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="e299b-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="e299b-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
