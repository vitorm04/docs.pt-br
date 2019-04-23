---
title: Método IHostAutoEvent::Set
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5af9f55bdcfe23f0b2a051b33cb1280f312820a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227009"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="3bf2f-102">Método IHostAutoEvent::Set</span><span class="sxs-lookup"><span data-stu-id="3bf2f-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="3bf2f-103">Define o atual [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instância para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bf2f-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3bf2f-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3bf2f-105">Return Value</span></span>  
  
|<span data-ttu-id="3bf2f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3bf2f-106">HRESULT</span></span>|<span data-ttu-id="3bf2f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bf2f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bf2f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bf2f-108">S_OK</span></span>|<span data-ttu-id="3bf2f-109">`Set` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="3bf2f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3bf2f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3bf2f-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3bf2f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3bf2f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3bf2f-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-113">The call timed out.</span></span>|  
|<span data-ttu-id="3bf2f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3bf2f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3bf2f-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3bf2f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3bf2f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3bf2f-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3bf2f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3bf2f-118">E_FAIL</span></span>|<span data-ttu-id="3bf2f-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3bf2f-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3bf2f-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3bf2f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bf2f-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3bf2f-122">Requirements</span></span>  
 <span data-ttu-id="3bf2f-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bf2f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bf2f-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bf2f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bf2f-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3bf2f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bf2f-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf2f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf2f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bf2f-127">See also</span></span>

- [<span data-ttu-id="3bf2f-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="3bf2f-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3bf2f-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="3bf2f-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3bf2f-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="3bf2f-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="3bf2f-131">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="3bf2f-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
