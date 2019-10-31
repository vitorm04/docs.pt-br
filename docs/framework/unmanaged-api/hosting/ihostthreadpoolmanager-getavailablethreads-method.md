---
title: Método IHostThreadPoolManager::GetAvailableThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: 21449d9365e6260267d3c79f384f6136ce894821
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122090"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="8903a-102">Método IHostThreadPoolManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="8903a-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="8903a-103">Obtém o número de threads no pool de threads que não estão processando itens de trabalho no momento.</span><span class="sxs-lookup"><span data-stu-id="8903a-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8903a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8903a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8903a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8903a-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="8903a-106">fora Ponteiro para o número de threads no pool de threads que não estão processando itens de trabalho no momento.</span><span class="sxs-lookup"><span data-stu-id="8903a-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8903a-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8903a-107">Return Value</span></span>  
  
|<span data-ttu-id="8903a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8903a-108">HRESULT</span></span>|<span data-ttu-id="8903a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8903a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8903a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8903a-110">S_OK</span></span>|<span data-ttu-id="8903a-111">`GetAvailableThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8903a-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8903a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8903a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8903a-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8903a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8903a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8903a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8903a-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8903a-115">The call timed out.</span></span>|  
|<span data-ttu-id="8903a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8903a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8903a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8903a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8903a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8903a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8903a-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="8903a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8903a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8903a-120">E_FAIL</span></span>|<span data-ttu-id="8903a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8903a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8903a-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="8903a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8903a-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8903a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8903a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8903a-124">E_NOTIMPL</span></span>|<span data-ttu-id="8903a-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="8903a-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8903a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="8903a-126">Remarks</span></span>  
 <span data-ttu-id="8903a-127">Se o host não fornecer uma implementação de `GetAvailableThreads`, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8903a-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8903a-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8903a-128">Requirements</span></span>  
 <span data-ttu-id="8903a-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8903a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8903a-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8903a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8903a-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8903a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8903a-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8903a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8903a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8903a-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="8903a-134">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="8903a-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
