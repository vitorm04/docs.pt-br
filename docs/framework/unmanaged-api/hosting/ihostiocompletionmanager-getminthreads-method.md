---
title: "Método IHostIoCompletionManager::GetMinThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f90a3f416520cc3f635f19d7ae34d5f9f304e9c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="801bf-102">Método IHostIoCompletionManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="801bf-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="801bf-103">Obtém o número mínimo de threads que o host fornece para processar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="801bf-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="801bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="801bf-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="801bf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="801bf-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="801bf-106">[out] Um ponteiro para o número mínimo de threads que o host fornece às solicitações de e/s do processo.</span><span class="sxs-lookup"><span data-stu-id="801bf-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="801bf-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="801bf-107">Return Value</span></span>  
  
|<span data-ttu-id="801bf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="801bf-108">HRESULT</span></span>|<span data-ttu-id="801bf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="801bf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="801bf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="801bf-110">S_OK</span></span>|<span data-ttu-id="801bf-111">`GetMinThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="801bf-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="801bf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="801bf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="801bf-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="801bf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="801bf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="801bf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="801bf-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="801bf-115">The call timed out.</span></span>|  
|<span data-ttu-id="801bf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="801bf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="801bf-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="801bf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="801bf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="801bf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="801bf-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="801bf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="801bf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="801bf-120">E_FAIL</span></span>|<span data-ttu-id="801bf-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="801bf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="801bf-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="801bf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="801bf-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="801bf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="801bf-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="801bf-124">E_NOTIMPL</span></span>|<span data-ttu-id="801bf-125">O host não fornece uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="801bf-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="801bf-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="801bf-126">Remarks</span></span>  
 <span data-ttu-id="801bf-127">Um host poderá controle exclusivo sobre o número de threads alocados para as solicitações de e/s de serviço, por motivos como implementação, o desempenho ou a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="801bf-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="801bf-128">Por esse motivo, o host não é necessário para implementar `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="801bf-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="801bf-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="801bf-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="801bf-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="801bf-130">Requirements</span></span>  
 <span data-ttu-id="801bf-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="801bf-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="801bf-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="801bf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="801bf-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="801bf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="801bf-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="801bf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="801bf-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="801bf-135">See Also</span></span>  
 [<span data-ttu-id="801bf-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="801bf-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="801bf-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="801bf-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
