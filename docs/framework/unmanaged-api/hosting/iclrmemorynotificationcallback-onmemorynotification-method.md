---
title: "Método ICLRMemoryNotificationCallback::OnMemoryNotification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback.OnMemoryNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 651dcd6380702a392d2dd06cf899ea567b004ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="09b3f-102">Método ICLRMemoryNotificationCallback::OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="09b3f-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="09b3f-103">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="09b3f-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09b3f-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09b3f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="09b3f-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="09b3f-106">[in] Uma da [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) valores, que indica a pressão de memória do computador no momento está enfrentando.</span><span class="sxs-lookup"><span data-stu-id="09b3f-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09b3f-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="09b3f-107">Return Value</span></span>  
  
|<span data-ttu-id="09b3f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09b3f-108">HRESULT</span></span>|<span data-ttu-id="09b3f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="09b3f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09b3f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="09b3f-110">S_OK</span></span>|<span data-ttu-id="09b3f-111">`OnMemoryNotification`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="09b3f-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="09b3f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09b3f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09b3f-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="09b3f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09b3f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09b3f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09b3f-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="09b3f-115">The call timed out.</span></span>|  
|<span data-ttu-id="09b3f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09b3f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09b3f-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="09b3f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09b3f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09b3f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09b3f-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="09b3f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09b3f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09b3f-120">E_FAIL</span></span>|<span data-ttu-id="09b3f-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="09b3f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09b3f-122">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="09b3f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09b3f-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="09b3f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09b3f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="09b3f-124">Remarks</span></span>  
 <span data-ttu-id="09b3f-125">O CLR registra um retorno de chamada para `OnMemoryNotification` usando uma chamada para o [Registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="09b3f-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="09b3f-126">O tempo de execução usa as informações retornadas no retorno de chamada para liberar memória adicional quando o host relata que a memória recursos executam baixo.</span><span class="sxs-lookup"><span data-stu-id="09b3f-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09b3f-127">Chamadas para `OnMemoryNotification` nunca bloquear.</span><span class="sxs-lookup"><span data-stu-id="09b3f-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="09b3f-128">Elas sempre retornam imediatamente.</span><span class="sxs-lookup"><span data-stu-id="09b3f-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b3f-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09b3f-129">Requirements</span></span>  
 <span data-ttu-id="09b3f-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09b3f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b3f-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09b3f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09b3f-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="09b3f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09b3f-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09b3f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b3f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09b3f-134">See Also</span></span>  
 [<span data-ttu-id="09b3f-135">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="09b3f-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="09b3f-136">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="09b3f-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="09b3f-137">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="09b3f-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
