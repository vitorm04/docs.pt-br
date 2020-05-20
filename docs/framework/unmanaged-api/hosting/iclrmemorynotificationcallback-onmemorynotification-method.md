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
ms.openlocfilehash: d88abcc523eca06c8ec50cac2d2984b26099174a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703795"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="83a4b-102">Método ICLRMemoryNotificationCallback::OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="83a4b-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="83a4b-103">Notifica o Common Language Runtime (CLR) da carga de memória no computador.</span><span class="sxs-lookup"><span data-stu-id="83a4b-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83a4b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83a4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83a4b-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="83a4b-106">no Um dos valores de [EMemoryAvailable](ememoryavailable-enumeration.md) , indicando a pressão de memória que o computador está enfrentando no momento.</span><span class="sxs-lookup"><span data-stu-id="83a4b-106">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83a4b-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="83a4b-107">Return Value</span></span>  
  
|<span data-ttu-id="83a4b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83a4b-108">HRESULT</span></span>|<span data-ttu-id="83a4b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="83a4b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83a4b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83a4b-110">S_OK</span></span>|<span data-ttu-id="83a4b-111">`OnMemoryNotification`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="83a4b-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="83a4b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83a4b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83a4b-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="83a4b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83a4b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83a4b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83a4b-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="83a4b-115">The call timed out.</span></span>|  
|<span data-ttu-id="83a4b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83a4b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83a4b-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="83a4b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83a4b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83a4b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83a4b-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="83a4b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83a4b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83a4b-120">E_FAIL</span></span>|<span data-ttu-id="83a4b-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="83a4b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83a4b-122">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="83a4b-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83a4b-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83a4b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83a4b-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="83a4b-124">Remarks</span></span>  
 <span data-ttu-id="83a4b-125">O CLR registra um retorno de chamada para `OnMemoryNotification` usando uma chamada para o método [IHostMemoryManager:: RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83a4b-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="83a4b-126">O tempo de execução usa as informações retornadas no retorno de chamada para liberar memória adicional quando o host relata que os recursos de memória estão em execução baixa.</span><span class="sxs-lookup"><span data-stu-id="83a4b-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83a4b-127">Chamadas para `OnMemoryNotification` nunca bloquear.</span><span class="sxs-lookup"><span data-stu-id="83a4b-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="83a4b-128">Eles sempre retornam imediatamente.</span><span class="sxs-lookup"><span data-stu-id="83a4b-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a4b-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83a4b-129">Requirements</span></span>  
 <span data-ttu-id="83a4b-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83a4b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a4b-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83a4b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83a4b-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83a4b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83a4b-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a4b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a4b-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="83a4b-134">See also</span></span>

- [<span data-ttu-id="83a4b-135">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="83a4b-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="83a4b-136">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="83a4b-136">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="83a4b-137">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="83a4b-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
