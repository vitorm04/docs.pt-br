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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973076"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="2605e-102">Método IHostIoCompletionManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="2605e-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="2605e-103">Obtém o número de threads de conclusão de e/s, do número total de threads gerenciados pelo host, que atualmente não estão atendendo a solicitações.</span><span class="sxs-lookup"><span data-stu-id="2605e-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2605e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2605e-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2605e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2605e-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="2605e-106">[out] Um ponteiro para o número de threads de conclusão de e/s gerenciados pelo host que estão atualmente disponíveis para solicitações de serviço.</span><span class="sxs-lookup"><span data-stu-id="2605e-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2605e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2605e-107">Return Value</span></span>  
  
|<span data-ttu-id="2605e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2605e-108">HRESULT</span></span>|<span data-ttu-id="2605e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2605e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2605e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2605e-110">S_OK</span></span>|<span data-ttu-id="2605e-111">`GetAvailableThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2605e-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2605e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2605e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2605e-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2605e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2605e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2605e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2605e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2605e-115">The call timed out.</span></span>|  
|<span data-ttu-id="2605e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2605e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2605e-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2605e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2605e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2605e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2605e-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="2605e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2605e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2605e-120">E_FAIL</span></span>|<span data-ttu-id="2605e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2605e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2605e-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="2605e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2605e-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2605e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2605e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2605e-124">E_NOTIMPL</span></span>|<span data-ttu-id="2605e-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="2605e-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2605e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="2605e-126">Remarks</span></span>  
 <span data-ttu-id="2605e-127">Um host pode querer controle exclusivo sobre o tamanho de pool de threads de conclusão e/s, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="2605e-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="2605e-128">Portanto, o host não é necessário para implementar `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="2605e-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="2605e-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="2605e-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2605e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2605e-130">Requirements</span></span>  
 <span data-ttu-id="2605e-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2605e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2605e-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2605e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2605e-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2605e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2605e-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2605e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2605e-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2605e-135">See also</span></span>

- [<span data-ttu-id="2605e-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="2605e-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="2605e-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="2605e-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
