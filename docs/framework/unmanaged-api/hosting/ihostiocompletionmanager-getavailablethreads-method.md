---
title: "Método IHostIoCompletionManager::GetAvailableThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f06e9fe0d07258fca107413d9ad328329b5456b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="2b2e3-102">Método IHostIoCompletionManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="2b2e3-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="2b2e3-103">Obtém o número de threads de conclusão de e/s, do número total de threads gerenciados pelo host, que atualmente não estão atendendo a solicitações.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b2e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b2e3-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b2e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b2e3-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="2b2e3-106">[out] Um ponteiro para o número de threads de conclusão de e/s gerenciados pelo host que estão atualmente disponíveis para solicitações de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b2e3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2b2e3-107">Return Value</span></span>  
  
|<span data-ttu-id="2b2e3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b2e3-108">HRESULT</span></span>|<span data-ttu-id="2b2e3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b2e3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b2e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b2e3-110">S_OK</span></span>|<span data-ttu-id="2b2e3-111">`GetAvailableThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2b2e3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b2e3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b2e3-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b2e3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b2e3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b2e3-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-115">The call timed out.</span></span>|  
|<span data-ttu-id="2b2e3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b2e3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b2e3-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b2e3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b2e3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b2e3-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b2e3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b2e3-120">E_FAIL</span></span>|<span data-ttu-id="2b2e3-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b2e3-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b2e3-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2b2e3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2b2e3-124">E_NOTIMPL</span></span>|<span data-ttu-id="2b2e3-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b2e3-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b2e3-126">Remarks</span></span>  
 <span data-ttu-id="2b2e3-127">Um host pode querer ter controle exclusivo sobre o tamanho do pool de threads de conclusão de e/s, por motivos como implementação, o desempenho ou a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="2b2e3-128">Portanto, o host não é necessário para implementar `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="2b2e3-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="2b2e3-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b2e3-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b2e3-130">Requirements</span></span>  
 <span data-ttu-id="2b2e3-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b2e3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b2e3-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b2e3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b2e3-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2b2e3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b2e3-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2e3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2e3-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b2e3-135">See Also</span></span>  
 [<span data-ttu-id="2b2e3-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="2b2e3-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="2b2e3-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="2b2e3-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
