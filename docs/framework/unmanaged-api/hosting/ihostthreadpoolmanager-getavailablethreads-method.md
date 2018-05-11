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
ms.openlocfilehash: a8350140bb0871acc560163848ac50eafef42f01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="11a10-102">Método IHostThreadPoolManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="11a10-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="11a10-103">Obtém o número de threads no pool de threads que não estão em processamento itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="11a10-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a10-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11a10-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11a10-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11a10-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="11a10-106">[out] Ponteiro para o número de threads no pool de threads que não estão em processamento itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="11a10-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11a10-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="11a10-107">Return Value</span></span>  
  
|<span data-ttu-id="11a10-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11a10-108">HRESULT</span></span>|<span data-ttu-id="11a10-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="11a10-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11a10-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="11a10-110">S_OK</span></span>|<span data-ttu-id="11a10-111">`GetAvailableThreads` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="11a10-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="11a10-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11a10-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11a10-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="11a10-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11a10-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11a10-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11a10-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="11a10-115">The call timed out.</span></span>|  
|<span data-ttu-id="11a10-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11a10-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11a10-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="11a10-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11a10-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11a10-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11a10-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="11a10-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11a10-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11a10-120">E_FAIL</span></span>|<span data-ttu-id="11a10-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="11a10-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11a10-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="11a10-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11a10-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11a10-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11a10-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="11a10-124">E_NOTIMPL</span></span>|<span data-ttu-id="11a10-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="11a10-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11a10-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="11a10-126">Remarks</span></span>  
 <span data-ttu-id="11a10-127">Se o host não fornecer uma implementação de `GetAvailableThreads`, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="11a10-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a10-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11a10-128">Requirements</span></span>  
 <span data-ttu-id="11a10-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11a10-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a10-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11a10-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11a10-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="11a10-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11a10-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a10-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a10-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11a10-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="11a10-134">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="11a10-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
