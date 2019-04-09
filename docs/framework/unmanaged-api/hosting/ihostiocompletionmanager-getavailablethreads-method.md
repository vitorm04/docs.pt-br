---
title: Método IHostIoCompletionManager::GetAvailableThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e96a12bbf9c4fdc8a0bc79661070eb7fec1a593
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123962"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="71d0f-102">Método IHostIoCompletionManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="71d0f-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="71d0f-103">Obtém o número de threads de conclusão de e/s, do número total de threads gerenciados pelo host, que atualmente não estão atendendo a solicitações.</span><span class="sxs-lookup"><span data-stu-id="71d0f-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71d0f-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71d0f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71d0f-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="71d0f-106">[out] Um ponteiro para o número de threads de conclusão de e/s gerenciados pelo host que estão atualmente disponíveis para solicitações de serviço.</span><span class="sxs-lookup"><span data-stu-id="71d0f-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71d0f-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="71d0f-107">Return Value</span></span>  
  
|<span data-ttu-id="71d0f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71d0f-108">HRESULT</span></span>|<span data-ttu-id="71d0f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="71d0f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71d0f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="71d0f-110">S_OK</span></span>|`GetAvailableThreads` <span data-ttu-id="71d0f-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="71d0f-111">returned successfully.</span></span>|  
|<span data-ttu-id="71d0f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71d0f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71d0f-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="71d0f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71d0f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71d0f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71d0f-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="71d0f-115">The call timed out.</span></span>|  
|<span data-ttu-id="71d0f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71d0f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71d0f-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="71d0f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71d0f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71d0f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71d0f-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="71d0f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71d0f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71d0f-120">E_FAIL</span></span>|<span data-ttu-id="71d0f-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="71d0f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71d0f-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="71d0f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71d0f-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="71d0f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="71d0f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="71d0f-124">E_NOTIMPL</span></span>|<span data-ttu-id="71d0f-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="71d0f-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71d0f-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="71d0f-126">Remarks</span></span>  
 <span data-ttu-id="71d0f-127">Um host pode querer controle exclusivo sobre o tamanho de pool de threads de conclusão e/s, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="71d0f-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="71d0f-128">Portanto, o host não é necessário para implementar `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="71d0f-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="71d0f-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="71d0f-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d0f-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71d0f-130">Requirements</span></span>  
 <span data-ttu-id="71d0f-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d0f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d0f-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71d0f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71d0f-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="71d0f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="71d0f-134">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="71d0f-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71d0f-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71d0f-135">See also</span></span>

- [<span data-ttu-id="71d0f-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="71d0f-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="71d0f-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="71d0f-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
