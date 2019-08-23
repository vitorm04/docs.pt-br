---
title: Método IHostMemoryManager::RegisterMemoryNotificationCallback
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34701642a9e76ec52141e00fe9dde92878faccd2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945444"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="c2597-102">Método IHostMemoryManager::RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="c2597-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="c2597-103">Registra um ponteiro para uma função de retorno de chamada que o host chama para notificar o Common Language Runtime (CLR) da carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="c2597-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2597-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2597-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2597-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2597-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="c2597-106">no Um ponteiro de interface para uma instância de [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) que é implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="c2597-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2597-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c2597-107">Return Value</span></span>  
  
|<span data-ttu-id="c2597-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2597-108">HRESULT</span></span>|<span data-ttu-id="c2597-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2597-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2597-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2597-110">S_OK</span></span>|<span data-ttu-id="c2597-111">`RegisterMemoryNotificationCallback`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2597-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="c2597-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2597-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2597-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2597-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2597-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2597-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2597-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c2597-115">The call timed out.</span></span>|  
|<span data-ttu-id="c2597-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2597-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2597-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c2597-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2597-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2597-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2597-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="c2597-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2597-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2597-120">E_FAIL</span></span>|<span data-ttu-id="c2597-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c2597-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2597-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="c2597-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2597-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2597-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2597-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2597-124">Remarks</span></span>  
 <span data-ttu-id="c2597-125">Como a `ICLRMemoryNotificationCallback` interface define apenas um método ([ICLRMemoryNotificationCallback:: OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) e, como `pCallback` é um ponteiro para uma `ICLRMemoryNotificationCallback` instância fornecida pelo CLR, o registro é efetivamente para a própria função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="c2597-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="c2597-126">O host é invocado `OnMemoryNotification` para relatar condições de pressão de memória, em vez de usar a função Win32 `CreateMemoryResourceNotification` padrão.</span><span class="sxs-lookup"><span data-stu-id="c2597-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="c2597-127">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="c2597-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2597-128">Chamadas para `OnMemoryNotification` nunca bloquear.</span><span class="sxs-lookup"><span data-stu-id="c2597-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="c2597-129">Eles sempre retornam imediatamente.</span><span class="sxs-lookup"><span data-stu-id="c2597-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2597-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2597-130">Requirements</span></span>  
 <span data-ttu-id="c2597-131">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2597-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2597-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2597-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2597-133">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c2597-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2597-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2597-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2597-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2597-135">See also</span></span>

- [<span data-ttu-id="c2597-136">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="c2597-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="c2597-137">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="c2597-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
