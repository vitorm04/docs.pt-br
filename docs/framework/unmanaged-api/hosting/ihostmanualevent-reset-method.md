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
ms.openlocfilehash: 9b3de70e6bdecba6370174ee825d2dec7c14270e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148558"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="b3e85-102">Método IHostManualEvent::Reset</span><span class="sxs-lookup"><span data-stu-id="b3e85-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="b3e85-103">Redefine o atual [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instância para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="b3e85-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3e85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3e85-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b3e85-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b3e85-105">Return Value</span></span>  
  
|<span data-ttu-id="b3e85-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3e85-106">HRESULT</span></span>|<span data-ttu-id="b3e85-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3e85-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3e85-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3e85-108">S_OK</span></span>|`Reset` <span data-ttu-id="b3e85-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b3e85-109">returned successfully.</span></span>|  
|<span data-ttu-id="b3e85-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3e85-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3e85-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b3e85-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3e85-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3e85-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3e85-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b3e85-113">The call timed out.</span></span>|  
|<span data-ttu-id="b3e85-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3e85-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3e85-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b3e85-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3e85-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3e85-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3e85-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b3e85-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3e85-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3e85-118">E_FAIL</span></span>|<span data-ttu-id="b3e85-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b3e85-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3e85-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b3e85-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3e85-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b3e85-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3e85-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3e85-122">Requirements</span></span>  
 <span data-ttu-id="b3e85-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3e85-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3e85-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3e85-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3e85-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b3e85-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b3e85-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b3e85-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3e85-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3e85-127">See also</span></span>

- [<span data-ttu-id="b3e85-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="b3e85-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b3e85-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="b3e85-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="b3e85-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="b3e85-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="b3e85-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="b3e85-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="b3e85-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="b3e85-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
