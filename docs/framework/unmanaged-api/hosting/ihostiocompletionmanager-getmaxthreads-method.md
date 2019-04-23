---
title: Método IHostIoCompletionManager::GetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8875fb24512ddfea57d5f9249e58de3c12b8c507
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119152"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="b1e97-102">Método IHostIoCompletionManager::GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="b1e97-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="b1e97-103">Obtém o número máximo de threads que o host pode alocar para atender a solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="b1e97-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1e97-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1e97-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1e97-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="b1e97-106">[out] Um ponteiro para o número máximo de threads no pool de threads que o host pode alocar para atender a solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="b1e97-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1e97-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b1e97-107">Return Value</span></span>  
  
|<span data-ttu-id="b1e97-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1e97-108">HRESULT</span></span>|<span data-ttu-id="b1e97-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1e97-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1e97-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1e97-110">S_OK</span></span>|<span data-ttu-id="b1e97-111">`GetMaxThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b1e97-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b1e97-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1e97-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1e97-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b1e97-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1e97-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1e97-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1e97-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b1e97-115">The call timed out.</span></span>|  
|<span data-ttu-id="b1e97-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1e97-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1e97-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b1e97-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1e97-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1e97-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1e97-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b1e97-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1e97-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1e97-120">E_FAIL</span></span>|<span data-ttu-id="b1e97-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b1e97-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1e97-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b1e97-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1e97-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b1e97-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1e97-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b1e97-124">E_NOTIMPL</span></span>|<span data-ttu-id="b1e97-125">O host não fornece uma implementação de `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="b1e97-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1e97-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1e97-126">Remarks</span></span>  
 <span data-ttu-id="b1e97-127">Um host poderá controle exclusivo sobre o número de threads que podem ser alocadas para processar solicitações de e/s, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="b1e97-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="b1e97-128">Por esse motivo, o host não é necessário para implementar `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="b1e97-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="b1e97-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="b1e97-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1e97-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1e97-130">Requirements</span></span>  
 <span data-ttu-id="b1e97-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1e97-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e97-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1e97-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1e97-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b1e97-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1e97-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e97-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e97-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1e97-135">See also</span></span>

- [<span data-ttu-id="b1e97-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b1e97-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b1e97-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b1e97-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
