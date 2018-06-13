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
ms.openlocfilehash: d68790cdb671efdd0761ceef59196e8646654d5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439589"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="55f1f-102">Método IHostMemoryManager::RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="55f1f-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="55f1f-103">Registra um ponteiro para uma função de retorno de chamada que invoca o host para notificar o common language runtime (CLR) da carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="55f1f-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f1f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55f1f-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55f1f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55f1f-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="55f1f-106">[in] Um ponteiro de interface para um [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instância que é implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="55f1f-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f1f-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="55f1f-107">Return Value</span></span>  
  
|<span data-ttu-id="55f1f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55f1f-108">HRESULT</span></span>|<span data-ttu-id="55f1f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="55f1f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55f1f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="55f1f-110">S_OK</span></span>|<span data-ttu-id="55f1f-111">`RegisterMemoryNotificationCallback` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="55f1f-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="55f1f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="55f1f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="55f1f-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="55f1f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="55f1f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="55f1f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="55f1f-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="55f1f-115">The call timed out.</span></span>|  
|<span data-ttu-id="55f1f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="55f1f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="55f1f-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="55f1f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="55f1f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="55f1f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="55f1f-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="55f1f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="55f1f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="55f1f-120">E_FAIL</span></span>|<span data-ttu-id="55f1f-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="55f1f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="55f1f-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="55f1f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="55f1f-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="55f1f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55f1f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="55f1f-124">Remarks</span></span>  
 <span data-ttu-id="55f1f-125">Porque o `ICLRMemoryNotificationCallback` interface define apenas um método ([Iclrmemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) e porque `pCallback` é um ponteiro para um `ICLRMemoryNotificationCallback` instância fornecida pelo CLR, o registro é efetivamente para a função de retorno de chamada em si.</span><span class="sxs-lookup"><span data-stu-id="55f1f-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="55f1f-126">Invoca o host `OnMemoryNotification` para condições de pressão de memória do relatório, em vez de usar o Win32 padrão `CreateMemoryResourceNotification` função.</span><span class="sxs-lookup"><span data-stu-id="55f1f-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="55f1f-127">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="55f1f-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55f1f-128">Chamadas para `OnMemoryNotification` nunca bloquear.</span><span class="sxs-lookup"><span data-stu-id="55f1f-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="55f1f-129">Elas sempre retornam imediatamente.</span><span class="sxs-lookup"><span data-stu-id="55f1f-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f1f-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55f1f-130">Requirements</span></span>  
 <span data-ttu-id="55f1f-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f1f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f1f-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="55f1f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55f1f-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="55f1f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55f1f-134">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f1f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f1f-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55f1f-135">See Also</span></span>  
 [<span data-ttu-id="55f1f-136">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="55f1f-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="55f1f-137">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="55f1f-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
