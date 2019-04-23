---
title: Método IHostIoCompletionManager::SetMinThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fd37546c63ef5e5f25686e105247555dfeb132a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222777"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="3b640-102">Método IHostIoCompletionManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="3b640-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="3b640-103">Define o número mínimo de threads que o host deve alocar até a conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="3b640-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b640-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b640-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b640-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b640-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="3b640-106">[in] O número mínimo de threads de conclusão de e/s que o host deve criar.</span><span class="sxs-lookup"><span data-stu-id="3b640-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b640-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3b640-107">Return Value</span></span>  
  
|<span data-ttu-id="3b640-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b640-108">HRESULT</span></span>|<span data-ttu-id="3b640-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b640-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b640-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b640-110">S_OK</span></span>|<span data-ttu-id="3b640-111">`SetMinThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3b640-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="3b640-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b640-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b640-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3b640-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b640-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b640-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b640-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3b640-115">The call timed out.</span></span>|  
|<span data-ttu-id="3b640-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b640-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b640-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3b640-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b640-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b640-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b640-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="3b640-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b640-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b640-120">E_FAIL</span></span>|<span data-ttu-id="3b640-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3b640-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3b640-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3b640-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b640-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3b640-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3b640-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3b640-124">E_NOTIMPL</span></span>|<span data-ttu-id="3b640-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="3b640-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b640-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b640-126">Remarks</span></span>  
 <span data-ttu-id="3b640-127">Um host poderá controle exclusivo sobre o número de threads que podem ser alocadas para processar solicitações de e/s, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="3b640-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="3b640-128">Por esse motivo, o host não é necessário para implementar `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="3b640-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="3b640-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="3b640-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b640-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b640-130">Requirements</span></span>  
 <span data-ttu-id="3b640-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b640-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b640-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3b640-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b640-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3b640-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b640-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b640-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b640-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b640-135">See also</span></span>

- [<span data-ttu-id="3b640-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="3b640-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3b640-137">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="3b640-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="3b640-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="3b640-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
