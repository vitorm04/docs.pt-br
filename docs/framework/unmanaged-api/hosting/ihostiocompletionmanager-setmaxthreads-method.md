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
ms.openlocfilehash: 345c7b88b6967773a185538943591383a686748c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224035"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="97475-102">Método IHostIoCompletionManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="97475-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="97475-103">Define o número máximo de threads que aloca o host para atender a solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="97475-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97475-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97475-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97475-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97475-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="97475-106">[in] O número máximo de threads para alocar para solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="97475-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97475-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="97475-107">Return Value</span></span>  
  
|<span data-ttu-id="97475-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97475-108">HRESULT</span></span>|<span data-ttu-id="97475-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="97475-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97475-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="97475-110">S_OK</span></span>|`SetMaxThreads` <span data-ttu-id="97475-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="97475-111">returned successfully.</span></span>|  
|<span data-ttu-id="97475-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97475-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97475-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="97475-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97475-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97475-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97475-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="97475-115">The call timed out.</span></span>|  
|<span data-ttu-id="97475-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97475-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97475-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="97475-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97475-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97475-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97475-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="97475-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97475-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97475-120">E_FAIL</span></span>|<span data-ttu-id="97475-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="97475-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97475-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="97475-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97475-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97475-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="97475-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="97475-124">E_NOTIMPL</span></span>|<span data-ttu-id="97475-125">O host não fornece uma implementação de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="97475-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97475-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="97475-126">Remarks</span></span>  
 `SetMaxThreads` <span data-ttu-id="97475-127">Fornece uma oportunidade para definir o número máximo de threads que estão disponíveis para atender a solicitações nas portas de e/s ao CLR.</span><span class="sxs-lookup"><span data-stu-id="97475-127">provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="97475-128">Um host pode precisar controle exclusivo sobre o tamanho do pool de threads, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="97475-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="97475-129">Por esse motivo, o host não é necessário para implementar `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="97475-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="97475-130">Nesse caso, um host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="97475-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97475-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97475-131">Requirements</span></span>  
 <span data-ttu-id="97475-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97475-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97475-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97475-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97475-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="97475-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="97475-135">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="97475-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97475-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97475-136">See also</span></span>

- [<span data-ttu-id="97475-137">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="97475-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="97475-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="97475-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
