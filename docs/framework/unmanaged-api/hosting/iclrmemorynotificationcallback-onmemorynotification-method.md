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
ms.openlocfilehash: 5c7866e0ecc62f037284a5329cb5785be90088f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115837"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="b109c-102">Método ICLRMemoryNotificationCallback::OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="b109c-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="b109c-103">Notifica o common language runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="b109c-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b109c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b109c-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b109c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b109c-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="b109c-106">[in] Um dos [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) valores, que indica a pressão de memória do computador no momento está enfrentando.</span><span class="sxs-lookup"><span data-stu-id="b109c-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b109c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b109c-107">Return Value</span></span>  
  
|<span data-ttu-id="b109c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b109c-108">HRESULT</span></span>|<span data-ttu-id="b109c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b109c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b109c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b109c-110">S_OK</span></span>|`OnMemoryNotification` <span data-ttu-id="b109c-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b109c-111">returned successfully.</span></span>|  
|<span data-ttu-id="b109c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b109c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b109c-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b109c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b109c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b109c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b109c-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b109c-115">The call timed out.</span></span>|  
|<span data-ttu-id="b109c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b109c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b109c-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b109c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b109c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b109c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b109c-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b109c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b109c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b109c-120">E_FAIL</span></span>|<span data-ttu-id="b109c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b109c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b109c-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b109c-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b109c-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b109c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b109c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="b109c-124">Remarks</span></span>  
 <span data-ttu-id="b109c-125">O CLR registra um retorno de chamada para `OnMemoryNotification` por meio de uma chamada para o [ihostmemorymanager:: Registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b109c-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="b109c-126">O tempo de execução usa as informações retornadas no retorno de chamada para liberar memória adicional quando o host informa que a memória recursos estão em execução baixo.</span><span class="sxs-lookup"><span data-stu-id="b109c-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b109c-127">Chamadas para `OnMemoryNotification` nunca bloquear.</span><span class="sxs-lookup"><span data-stu-id="b109c-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="b109c-128">Elas sempre retornam imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b109c-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b109c-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b109c-129">Requirements</span></span>  
 <span data-ttu-id="b109c-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b109c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b109c-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b109c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b109c-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b109c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b109c-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b109c-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b109c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b109c-134">See also</span></span>

- [<span data-ttu-id="b109c-135">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="b109c-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="b109c-136">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="b109c-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="b109c-137">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="b109c-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
