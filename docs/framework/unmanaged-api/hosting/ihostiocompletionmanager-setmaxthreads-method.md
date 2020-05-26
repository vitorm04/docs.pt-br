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
ms.openlocfilehash: 55727903a7f3c798e7472de6de5249de98af7ae7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804671"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="06807-102">Método IHostIoCompletionManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="06807-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="06807-103">Define o número máximo de threads que o host aloca para atender às solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="06807-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06807-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06807-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06807-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06807-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="06807-106">no O número máximo de threads a serem alocados para solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="06807-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06807-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="06807-107">Return Value</span></span>  
  
|<span data-ttu-id="06807-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06807-108">HRESULT</span></span>|<span data-ttu-id="06807-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="06807-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06807-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="06807-110">S_OK</span></span>|<span data-ttu-id="06807-111">`SetMaxThreads`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="06807-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="06807-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="06807-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="06807-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="06807-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="06807-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="06807-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="06807-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="06807-115">The call timed out.</span></span>|  
|<span data-ttu-id="06807-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="06807-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="06807-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="06807-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="06807-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="06807-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="06807-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="06807-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="06807-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="06807-120">E_FAIL</span></span>|<span data-ttu-id="06807-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="06807-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="06807-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="06807-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="06807-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="06807-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="06807-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="06807-124">E_NOTIMPL</span></span>|<span data-ttu-id="06807-125">O host não fornece uma implementação de `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="06807-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06807-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="06807-126">Remarks</span></span>  
 <span data-ttu-id="06807-127">`SetMaxThreads`fornece ao CLR uma oportunidade para definir o número máximo de threads que estão disponíveis para solicitações de serviço em portas de e/s.</span><span class="sxs-lookup"><span data-stu-id="06807-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="06807-128">Um host pode precisar de controle exclusivo sobre o tamanho do pool de threads, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="06807-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="06807-129">Por esse motivo, o host não precisa implementar `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="06807-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="06807-130">Nesse caso, um host deve retornar E_NOTIMPL desse método.</span><span class="sxs-lookup"><span data-stu-id="06807-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06807-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06807-131">Requirements</span></span>  
 <span data-ttu-id="06807-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06807-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06807-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="06807-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06807-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="06807-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06807-135">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06807-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06807-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="06807-136">See also</span></span>

- [<span data-ttu-id="06807-137">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="06807-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="06807-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="06807-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
