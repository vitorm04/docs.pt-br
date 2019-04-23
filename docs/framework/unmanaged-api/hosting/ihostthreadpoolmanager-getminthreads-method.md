---
title: Método IHostThreadPoolManager::GetMinThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1230a72d06677b4d36d10a8a31d63638c1fcd41
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170684"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="4bdce-102">Método IHostThreadPoolManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="4bdce-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="4bdce-103">Obtém o número mínimo de threads ociosos do que o host mantém no pool de threads em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="4bdce-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bdce-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bdce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4bdce-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="4bdce-106">[out] Um ponteiro para o número mínimo de threads de trabalho ocioso que atualmente mantém o host.</span><span class="sxs-lookup"><span data-stu-id="4bdce-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdce-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4bdce-107">Return Value</span></span>  
  
|<span data-ttu-id="4bdce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bdce-108">HRESULT</span></span>|<span data-ttu-id="4bdce-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bdce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bdce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bdce-110">S_OK</span></span>|<span data-ttu-id="4bdce-111">`GetMinThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4bdce-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4bdce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bdce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bdce-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4bdce-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bdce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bdce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bdce-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4bdce-115">The call timed out.</span></span>|  
|<span data-ttu-id="4bdce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bdce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bdce-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4bdce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bdce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bdce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bdce-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="4bdce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bdce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bdce-120">E_FAIL</span></span>|<span data-ttu-id="4bdce-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4bdce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bdce-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4bdce-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bdce-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4bdce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4bdce-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4bdce-124">E_NOTIMPL</span></span>|<span data-ttu-id="4bdce-125">O host não fornece uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4bdce-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdce-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bdce-126">Remarks</span></span>  
 <span data-ttu-id="4bdce-127">O host não é necessário para fornecer uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4bdce-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="4bdce-128">Nesse caso, ele deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4bdce-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdce-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bdce-129">Requirements</span></span>  
 <span data-ttu-id="4bdce-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdce-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdce-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bdce-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bdce-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4bdce-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdce-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdce-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdce-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bdce-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4bdce-135">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="4bdce-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="4bdce-136">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="4bdce-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="4bdce-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="4bdce-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
