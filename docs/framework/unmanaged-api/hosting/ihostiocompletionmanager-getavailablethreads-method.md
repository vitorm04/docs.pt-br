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
ms.openlocfilehash: 0ef25267f6af5d1f8503825e2784383a0eb241e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535523"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="e13f6-102">Método IHostIoCompletionManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="e13f6-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="e13f6-103">Obtém o número de threads de conclusão de e/s, do número total de threads gerenciados pelo host, que atualmente não estão atendendo a solicitações.</span><span class="sxs-lookup"><span data-stu-id="e13f6-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e13f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e13f6-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e13f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e13f6-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="e13f6-106">[out] Um ponteiro para o número de threads de conclusão de e/s gerenciados pelo host que estão atualmente disponíveis para solicitações de serviço.</span><span class="sxs-lookup"><span data-stu-id="e13f6-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e13f6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e13f6-107">Return Value</span></span>  
  
|<span data-ttu-id="e13f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e13f6-108">HRESULT</span></span>|<span data-ttu-id="e13f6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e13f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e13f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e13f6-110">S_OK</span></span>|<span data-ttu-id="e13f6-111">`GetAvailableThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e13f6-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e13f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e13f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e13f6-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e13f6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e13f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e13f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e13f6-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e13f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="e13f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e13f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e13f6-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e13f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e13f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e13f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e13f6-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e13f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e13f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e13f6-120">E_FAIL</span></span>|<span data-ttu-id="e13f6-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e13f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e13f6-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e13f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e13f6-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e13f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e13f6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e13f6-124">E_NOTIMPL</span></span>|<span data-ttu-id="e13f6-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="e13f6-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e13f6-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e13f6-126">Remarks</span></span>  
 <span data-ttu-id="e13f6-127">Um host pode querer controle exclusivo sobre o tamanho de pool de threads de conclusão e/s, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="e13f6-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e13f6-128">Portanto, o host não é necessário para implementar `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="e13f6-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="e13f6-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="e13f6-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e13f6-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e13f6-130">Requirements</span></span>  
 <span data-ttu-id="e13f6-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e13f6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e13f6-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e13f6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e13f6-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e13f6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e13f6-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e13f6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e13f6-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e13f6-135">See also</span></span>
- [<span data-ttu-id="e13f6-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e13f6-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e13f6-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e13f6-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
