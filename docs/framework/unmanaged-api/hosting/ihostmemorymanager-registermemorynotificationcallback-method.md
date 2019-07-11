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
ms.openlocfilehash: 48580f5ac71b906c302ee7ce1b98e7d4334f2482
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767729"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="b4663-102">Método IHostMemoryManager::RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="b4663-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="b4663-103">Registra um ponteiro para uma função de retorno de chamada que o host chama para notificar o common language runtime (CLR) da carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="b4663-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4663-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4663-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4663-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4663-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="b4663-106">[in] Um ponteiro de interface para um [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instância que é implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="b4663-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4663-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b4663-107">Return Value</span></span>  
  
|<span data-ttu-id="b4663-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4663-108">HRESULT</span></span>|<span data-ttu-id="b4663-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4663-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4663-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4663-110">S_OK</span></span>|<span data-ttu-id="b4663-111">`RegisterMemoryNotificationCallback` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b4663-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="b4663-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4663-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4663-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b4663-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b4663-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4663-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b4663-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b4663-115">The call timed out.</span></span>|  
|<span data-ttu-id="b4663-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4663-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b4663-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b4663-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b4663-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b4663-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b4663-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b4663-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b4663-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4663-120">E_FAIL</span></span>|<span data-ttu-id="b4663-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b4663-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b4663-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b4663-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b4663-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b4663-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4663-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4663-124">Remarks</span></span>  
 <span data-ttu-id="b4663-125">Porque o `ICLRMemoryNotificationCallback` interface define apenas um método ([iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) e porque `pCallback` é um ponteiro para um `ICLRMemoryNotificationCallback` instância fornecida pelo CLR, o registro é efetivamente para a função de retorno de chamada em si.</span><span class="sxs-lookup"><span data-stu-id="b4663-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="b4663-126">O host invoca `OnMemoryNotification` para relatar condições de pressão de memória, em vez de usar o Win32 padrão `CreateMemoryResourceNotification` função.</span><span class="sxs-lookup"><span data-stu-id="b4663-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="b4663-127">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="b4663-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4663-128">Chamadas para `OnMemoryNotification` nunca bloquear.</span><span class="sxs-lookup"><span data-stu-id="b4663-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="b4663-129">Elas sempre retornam imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b4663-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4663-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4663-130">Requirements</span></span>  
 <span data-ttu-id="b4663-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4663-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4663-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4663-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4663-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b4663-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4663-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4663-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4663-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4663-135">See also</span></span>

- [<span data-ttu-id="b4663-136">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="b4663-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="b4663-137">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="b4663-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
