---
title: "Método IHostIoCompletionManager::SetMaxThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d2d8436d85f7be40c89693628794b007e0c6a88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="c06bc-102">Método IHostIoCompletionManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="c06bc-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="c06bc-103">Define o número máximo de threads que o host aloca solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="c06bc-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c06bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c06bc-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c06bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c06bc-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="c06bc-106">[in] O número máximo de threads para alocar para solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="c06bc-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c06bc-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c06bc-107">Return Value</span></span>  
  
|<span data-ttu-id="c06bc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c06bc-108">HRESULT</span></span>|<span data-ttu-id="c06bc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c06bc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c06bc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c06bc-110">S_OK</span></span>|<span data-ttu-id="c06bc-111">`SetMaxThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c06bc-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="c06bc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c06bc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c06bc-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c06bc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c06bc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c06bc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c06bc-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="c06bc-115">The call timed out.</span></span>|  
|<span data-ttu-id="c06bc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c06bc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c06bc-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c06bc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c06bc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c06bc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c06bc-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="c06bc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c06bc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c06bc-120">E_FAIL</span></span>|<span data-ttu-id="c06bc-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c06bc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c06bc-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c06bc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c06bc-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c06bc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c06bc-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c06bc-124">E_NOTIMPL</span></span>|<span data-ttu-id="c06bc-125">O host não fornece uma implementação de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="c06bc-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c06bc-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="c06bc-126">Remarks</span></span>  
 <span data-ttu-id="c06bc-127">`SetMaxThreads`fornece o CLR a oportunidade de definir o número máximo de threads que estão disponíveis para atender a solicitações nas portas de e/s.</span><span class="sxs-lookup"><span data-stu-id="c06bc-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="c06bc-128">Um host talvez seja necessário controle exclusivo sobre o tamanho do pool de threads, por motivos como implementação, o desempenho ou a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="c06bc-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="c06bc-129">Por esse motivo, o host não é necessário para implementar `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="c06bc-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="c06bc-130">Nesse caso, um host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="c06bc-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c06bc-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c06bc-131">Requirements</span></span>  
 <span data-ttu-id="c06bc-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c06bc-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c06bc-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c06bc-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c06bc-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c06bc-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c06bc-135">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c06bc-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c06bc-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c06bc-136">See Also</span></span>  
 [<span data-ttu-id="c06bc-137">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="c06bc-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="c06bc-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="c06bc-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
