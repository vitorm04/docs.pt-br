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
ms.openlocfilehash: 2fa429979faa04518397cf58aaa62d3e45230a76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133843"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="885ca-102">Método IHostIoCompletionManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="885ca-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="885ca-103">Obtém o número de threads de conclusão de e/s do número total de threads gerenciados pelo host, que não estão atendendo às solicitações no momento.</span><span class="sxs-lookup"><span data-stu-id="885ca-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="885ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="885ca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="885ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="885ca-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="885ca-106">fora Um ponteiro para o número de threads de conclusão de e/s gerenciados pelo host que estão disponíveis no momento para solicitações de serviço.</span><span class="sxs-lookup"><span data-stu-id="885ca-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="885ca-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="885ca-107">Return Value</span></span>  
  
|<span data-ttu-id="885ca-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="885ca-108">HRESULT</span></span>|<span data-ttu-id="885ca-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="885ca-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="885ca-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="885ca-110">S_OK</span></span>|<span data-ttu-id="885ca-111">`GetAvailableThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="885ca-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="885ca-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="885ca-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="885ca-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="885ca-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="885ca-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="885ca-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="885ca-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="885ca-115">The call timed out.</span></span>|  
|<span data-ttu-id="885ca-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="885ca-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="885ca-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="885ca-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="885ca-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="885ca-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="885ca-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="885ca-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="885ca-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="885ca-120">E_FAIL</span></span>|<span data-ttu-id="885ca-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="885ca-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="885ca-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="885ca-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="885ca-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="885ca-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="885ca-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="885ca-124">E_NOTIMPL</span></span>|<span data-ttu-id="885ca-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="885ca-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="885ca-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="885ca-126">Remarks</span></span>  
 <span data-ttu-id="885ca-127">Um host pode querer um controle exclusivo sobre o tamanho do pool de threads de conclusão de e/s, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="885ca-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="885ca-128">Portanto, o host não é necessário para implementar `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="885ca-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="885ca-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="885ca-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="885ca-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="885ca-130">Requirements</span></span>  
 <span data-ttu-id="885ca-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="885ca-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="885ca-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="885ca-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="885ca-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="885ca-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="885ca-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="885ca-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="885ca-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="885ca-135">See also</span></span>

- [<span data-ttu-id="885ca-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="885ca-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="885ca-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="885ca-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
