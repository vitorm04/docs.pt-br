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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cb2c7aa5b2bb301cf047ee465ac2e3a755974e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615291"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="163e2-102">Método IHostThreadPoolManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="163e2-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="163e2-103">Obtém o número de threads no pool de threads que não estão processando no momento, os itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="163e2-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="163e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="163e2-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="163e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="163e2-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="163e2-106">[out] Ponteiro para o número de threads no pool de threads que não estão processando no momento, os itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="163e2-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="163e2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="163e2-107">Return Value</span></span>  
  
|<span data-ttu-id="163e2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="163e2-108">HRESULT</span></span>|<span data-ttu-id="163e2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="163e2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="163e2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="163e2-110">S_OK</span></span>|<span data-ttu-id="163e2-111">`GetAvailableThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="163e2-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="163e2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="163e2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="163e2-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="163e2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="163e2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="163e2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="163e2-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="163e2-115">The call timed out.</span></span>|  
|<span data-ttu-id="163e2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="163e2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="163e2-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="163e2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="163e2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="163e2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="163e2-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="163e2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="163e2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="163e2-120">E_FAIL</span></span>|<span data-ttu-id="163e2-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="163e2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="163e2-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="163e2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="163e2-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="163e2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="163e2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="163e2-124">E_NOTIMPL</span></span>|<span data-ttu-id="163e2-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="163e2-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="163e2-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="163e2-126">Remarks</span></span>  
 <span data-ttu-id="163e2-127">Se o host não fornecer uma implementação de `GetAvailableThreads`, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="163e2-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="163e2-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="163e2-128">Requirements</span></span>  
 <span data-ttu-id="163e2-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="163e2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="163e2-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="163e2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="163e2-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="163e2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="163e2-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="163e2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="163e2-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="163e2-133">See also</span></span>
- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="163e2-134">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="163e2-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
