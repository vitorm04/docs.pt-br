---
title: Método IHostIoCompletionManager::SetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a810f3a25dc90ddb234c70ca3fa5130039350136
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438815"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="abfa9-102">Método IHostIoCompletionManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="abfa9-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="abfa9-103">Define o número máximo de threads que o host aloca solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="abfa9-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abfa9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abfa9-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abfa9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="abfa9-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="abfa9-106">[in] O número máximo de threads para alocar para solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="abfa9-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abfa9-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="abfa9-107">Return Value</span></span>  
  
|<span data-ttu-id="abfa9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abfa9-108">HRESULT</span></span>|<span data-ttu-id="abfa9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="abfa9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abfa9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="abfa9-110">S_OK</span></span>|<span data-ttu-id="abfa9-111">`SetMaxThreads` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="abfa9-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="abfa9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="abfa9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="abfa9-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="abfa9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="abfa9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="abfa9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="abfa9-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="abfa9-115">The call timed out.</span></span>|  
|<span data-ttu-id="abfa9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="abfa9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="abfa9-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="abfa9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="abfa9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="abfa9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="abfa9-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="abfa9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="abfa9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="abfa9-120">E_FAIL</span></span>|<span data-ttu-id="abfa9-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="abfa9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="abfa9-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="abfa9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="abfa9-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="abfa9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="abfa9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="abfa9-124">E_NOTIMPL</span></span>|<span data-ttu-id="abfa9-125">O host não fornece uma implementação de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="abfa9-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abfa9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="abfa9-126">Remarks</span></span>  
 <span data-ttu-id="abfa9-127">`SetMaxThreads` fornece o CLR a oportunidade de definir o número máximo de threads que estão disponíveis para atender a solicitações nas portas de e/s.</span><span class="sxs-lookup"><span data-stu-id="abfa9-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="abfa9-128">Um host talvez seja necessário controle exclusivo sobre o tamanho do pool de threads, por motivos como implementação, o desempenho ou a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="abfa9-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="abfa9-129">Por esse motivo, o host não é necessário para implementar `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="abfa9-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="abfa9-130">Nesse caso, um host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="abfa9-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abfa9-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abfa9-131">Requirements</span></span>  
 <span data-ttu-id="abfa9-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abfa9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abfa9-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="abfa9-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abfa9-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="abfa9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abfa9-135">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abfa9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abfa9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abfa9-136">See Also</span></span>  
 [<span data-ttu-id="abfa9-137">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="abfa9-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="abfa9-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="abfa9-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
