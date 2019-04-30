---
title: Método IHostThreadPoolManager::GetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4dce4efeb82f44e2c0d19e95551696b16e9f07ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961187"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="656e9-102">Método IHostThreadPoolManager::GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="656e9-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="656e9-103">Obtém o número máximo de threads que o host mantém simultaneamente no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="656e9-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="656e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="656e9-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="656e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="656e9-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="656e9-106">[out] Um ponteiro para o número máximo de threads que o host mantém no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="656e9-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="656e9-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="656e9-107">Return Value</span></span>  
  
|<span data-ttu-id="656e9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="656e9-108">HRESULT</span></span>|<span data-ttu-id="656e9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="656e9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="656e9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="656e9-110">S_OK</span></span>|<span data-ttu-id="656e9-111">`GetMaxThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="656e9-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="656e9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="656e9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="656e9-113">O common language runtime (CLR (não foi carregado em um processo, ou o CLR está em um estado no qual ele não pode executar código gerenciado ou o processo de chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="656e9-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="656e9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="656e9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="656e9-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="656e9-115">The call timed out.</span></span>|  
|<span data-ttu-id="656e9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="656e9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="656e9-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="656e9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="656e9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="656e9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="656e9-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="656e9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="656e9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="656e9-120">E_FAIL</span></span>|<span data-ttu-id="656e9-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="656e9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="656e9-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="656e9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="656e9-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="656e9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="656e9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="656e9-124">E_NOTIMPL</span></span>|<span data-ttu-id="656e9-125">O host não fornece uma implementação de `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="656e9-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="656e9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="656e9-126">Remarks</span></span>  
 <span data-ttu-id="656e9-127">O CLR chama `GetMaxThreads` para determinar o número total de threads no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="656e9-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="656e9-128">O [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) método obtém o número de threads que não estão processando no momento, os itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="656e9-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="656e9-129">Todas as solicitações acima do valor retornado do `pdwMaxWorkerThreads` parâmetro permanecem na fila até que os threads se tornem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="656e9-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="656e9-130">Se o host não fornecer uma implementação de `GetMaxThreads`, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="656e9-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="656e9-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="656e9-131">Requirements</span></span>  
 <span data-ttu-id="656e9-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="656e9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="656e9-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="656e9-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="656e9-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="656e9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="656e9-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="656e9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656e9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="656e9-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="656e9-137">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="656e9-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="656e9-138">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="656e9-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="656e9-139">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="656e9-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
