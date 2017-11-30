---
title: "Método IHostIoCompletionManager::SetMinThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8903aa2f2119ad3c4dceebfaba9ede26200e899
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="8803d-102">Método IHostIoCompletionManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="8803d-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="8803d-103">Define o número mínimo de threads que o host deve alocar até a conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="8803d-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8803d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8803d-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8803d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8803d-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="8803d-106">[in] O número mínimo de threads de conclusão de e/s que o host deve criar.</span><span class="sxs-lookup"><span data-stu-id="8803d-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8803d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8803d-107">Return Value</span></span>  
  
|<span data-ttu-id="8803d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8803d-108">HRESULT</span></span>|<span data-ttu-id="8803d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8803d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8803d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8803d-110">S_OK</span></span>|<span data-ttu-id="8803d-111">`SetMinThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="8803d-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8803d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8803d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8803d-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8803d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8803d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8803d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8803d-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="8803d-115">The call timed out.</span></span>|  
|<span data-ttu-id="8803d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8803d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8803d-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8803d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8803d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8803d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8803d-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="8803d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8803d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8803d-120">E_FAIL</span></span>|<span data-ttu-id="8803d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8803d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8803d-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8803d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8803d-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8803d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8803d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8803d-124">E_NOTIMPL</span></span>|<span data-ttu-id="8803d-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="8803d-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8803d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="8803d-126">Remarks</span></span>  
 <span data-ttu-id="8803d-127">Um host poderá controle exclusivo sobre o número de threads que podem ser alocadas para processar solicitações de e/s, por motivos como implementação, o desempenho ou a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="8803d-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="8803d-128">Por esse motivo, o host não é necessário para implementar `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="8803d-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="8803d-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="8803d-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8803d-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8803d-130">Requirements</span></span>  
 <span data-ttu-id="8803d-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8803d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8803d-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8803d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8803d-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8803d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8803d-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8803d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8803d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8803d-135">See Also</span></span>  
 [<span data-ttu-id="8803d-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="8803d-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="8803d-137">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="8803d-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="8803d-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="8803d-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
