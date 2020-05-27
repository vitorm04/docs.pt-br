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
ms.openlocfilehash: b5cd02f54a930942e1892f88fb3d8e926a6f3e1b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804563"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="2c339-102">Método IHostManualEvent::Set</span><span class="sxs-lookup"><span data-stu-id="2c339-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="2c339-103">Define a instância de [IHostManualEvent](ihostmanualevent-interface.md) atual para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="2c339-103">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c339-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c339-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2c339-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2c339-105">Return Value</span></span>  
  
|<span data-ttu-id="2c339-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c339-106">HRESULT</span></span>|<span data-ttu-id="2c339-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c339-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c339-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c339-108">S_OK</span></span>|<span data-ttu-id="2c339-109">`Set`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2c339-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="2c339-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c339-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c339-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2c339-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c339-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c339-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c339-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2c339-113">The call timed out.</span></span>|  
|<span data-ttu-id="2c339-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c339-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c339-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2c339-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c339-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c339-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c339-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="2c339-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c339-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c339-118">E_FAIL</span></span>|<span data-ttu-id="2c339-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2c339-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c339-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="2c339-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c339-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2c339-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c339-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c339-122">Requirements</span></span>  
 <span data-ttu-id="2c339-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c339-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c339-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2c339-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c339-125">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2c339-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c339-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c339-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c339-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c339-127">See also</span></span>

- [<span data-ttu-id="2c339-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="2c339-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2c339-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="2c339-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2c339-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="2c339-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2c339-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="2c339-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="2c339-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="2c339-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
