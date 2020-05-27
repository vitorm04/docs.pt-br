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
ms.openlocfilehash: efbfa310c90f48c99219cb185f090a1b854949a2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842277"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="9f65a-102">Método IHostThreadPoolManager::GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9f65a-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="9f65a-103">Obtém o número máximo de threads que o host mantém simultaneamente no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="9f65a-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f65a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f65a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f65a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f65a-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="9f65a-106">fora Um ponteiro para o número máximo de threads que o host mantém no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="9f65a-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f65a-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="9f65a-107">Return Value</span></span>  
  
|<span data-ttu-id="9f65a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f65a-108">HRESULT</span></span>|<span data-ttu-id="9f65a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f65a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f65a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f65a-110">S_OK</span></span>|<span data-ttu-id="9f65a-111">`GetMaxThreads`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9f65a-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9f65a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f65a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f65a-113">O Common Language Runtime (CLR (não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9f65a-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9f65a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f65a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9f65a-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9f65a-115">The call timed out.</span></span>|  
|<span data-ttu-id="9f65a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9f65a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9f65a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9f65a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9f65a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9f65a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9f65a-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9f65a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9f65a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9f65a-120">E_FAIL</span></span>|<span data-ttu-id="9f65a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9f65a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9f65a-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9f65a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9f65a-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9f65a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9f65a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9f65a-124">E_NOTIMPL</span></span>|<span data-ttu-id="9f65a-125">O host não fornece uma implementação de `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="9f65a-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f65a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f65a-126">Remarks</span></span>  
 <span data-ttu-id="9f65a-127">O CLR chama `GetMaxThreads` para determinar o número total de threads no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="9f65a-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="9f65a-128">O método [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) Obtém o número de threads que não estão processando itens de trabalho no momento.</span><span class="sxs-lookup"><span data-stu-id="9f65a-128">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="9f65a-129">Todas as solicitações acima do valor retornado do `pdwMaxWorkerThreads` parâmetro permanecem enfileiradas até que os threads se tornem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9f65a-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="9f65a-130">Se o host não fornecer uma implementação de `GetMaxThreads` , ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="9f65a-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f65a-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f65a-131">Requirements</span></span>  
 <span data-ttu-id="9f65a-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f65a-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f65a-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9f65a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f65a-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9f65a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f65a-135">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f65a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f65a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f65a-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="9f65a-137">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="9f65a-137">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="9f65a-138">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9f65a-138">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="9f65a-139">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="9f65a-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
