---
title: Método ICLRMemoryNotificationCallback::OnMemoryNotification
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 187c0a8d929958b7eaf1e99771da6a0d29c3d5f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434181"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="34a17-102">Método ICLRMemoryNotificationCallback::OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="34a17-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="34a17-103">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="34a17-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34a17-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34a17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a17-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="34a17-106">[in] Uma da [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) valores, que indica a pressão de memória do computador no momento está enfrentando.</span><span class="sxs-lookup"><span data-stu-id="34a17-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34a17-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="34a17-107">Return Value</span></span>  
  
|<span data-ttu-id="34a17-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34a17-108">HRESULT</span></span>|<span data-ttu-id="34a17-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="34a17-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34a17-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="34a17-110">S_OK</span></span>|<span data-ttu-id="34a17-111">`OnMemoryNotification` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="34a17-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="34a17-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34a17-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34a17-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="34a17-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34a17-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34a17-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34a17-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="34a17-115">The call timed out.</span></span>|  
|<span data-ttu-id="34a17-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34a17-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34a17-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="34a17-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34a17-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34a17-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34a17-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="34a17-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34a17-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34a17-120">E_FAIL</span></span>|<span data-ttu-id="34a17-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="34a17-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34a17-122">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="34a17-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34a17-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34a17-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34a17-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="34a17-124">Remarks</span></span>  
 <span data-ttu-id="34a17-125">O CLR registra um retorno de chamada para `OnMemoryNotification` usando uma chamada para o [Registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="34a17-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="34a17-126">O tempo de execução usa as informações retornadas no retorno de chamada para liberar memória adicional quando o host relata que a memória recursos executam baixo.</span><span class="sxs-lookup"><span data-stu-id="34a17-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34a17-127">Chamadas para `OnMemoryNotification` nunca bloquear.</span><span class="sxs-lookup"><span data-stu-id="34a17-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="34a17-128">Elas sempre retornam imediatamente.</span><span class="sxs-lookup"><span data-stu-id="34a17-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34a17-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34a17-129">Requirements</span></span>  
 <span data-ttu-id="34a17-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34a17-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34a17-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34a17-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34a17-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="34a17-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34a17-133">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34a17-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a17-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a17-134">See Also</span></span>  
 [<span data-ttu-id="34a17-135">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="34a17-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="34a17-136">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="34a17-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="34a17-137">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="34a17-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
