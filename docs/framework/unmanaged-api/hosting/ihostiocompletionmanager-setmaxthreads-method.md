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
ms.openlocfilehash: 7a16c141d9d07af82bd984955e06199e66ce3bbf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133757"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="8c0c2-102">Método IHostIoCompletionManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="8c0c2-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="8c0c2-103">Define o número máximo de threads que o host aloca para atender às solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c0c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c0c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c0c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c0c2-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="8c0c2-106">no O número máximo de threads a serem alocados para solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c0c2-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8c0c2-107">Return Value</span></span>  
  
|<span data-ttu-id="8c0c2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c0c2-108">HRESULT</span></span>|<span data-ttu-id="8c0c2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c0c2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c0c2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c0c2-110">S_OK</span></span>|<span data-ttu-id="8c0c2-111">`SetMaxThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8c0c2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c0c2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c0c2-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c0c2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c0c2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c0c2-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-115">The call timed out.</span></span>|  
|<span data-ttu-id="8c0c2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c0c2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c0c2-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c0c2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c0c2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c0c2-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c0c2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c0c2-120">E_FAIL</span></span>|<span data-ttu-id="8c0c2-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c0c2-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c0c2-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8c0c2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8c0c2-124">E_NOTIMPL</span></span>|<span data-ttu-id="8c0c2-125">O host não fornece uma implementação de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c0c2-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c0c2-126">Remarks</span></span>  
 <span data-ttu-id="8c0c2-127">`SetMaxThreads` fornece ao CLR uma oportunidade para definir o número máximo de threads que estão disponíveis para solicitações de serviço em portas de e/s.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="8c0c2-128">Um host pode precisar de controle exclusivo sobre o tamanho do pool de threads, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="8c0c2-129">Por esse motivo, o host não é necessário para implementar `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="8c0c2-130">Nesse caso, um host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="8c0c2-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c0c2-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c0c2-131">Requirements</span></span>  
 <span data-ttu-id="8c0c2-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c0c2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c0c2-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c0c2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c0c2-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c0c2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c0c2-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c0c2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0c2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c0c2-136">See also</span></span>

- [<span data-ttu-id="8c0c2-137">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="8c0c2-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="8c0c2-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="8c0c2-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
