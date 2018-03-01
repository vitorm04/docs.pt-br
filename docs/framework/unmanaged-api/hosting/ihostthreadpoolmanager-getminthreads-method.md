---
title: "Método IHostThreadPoolManager::GetMinThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 393400c7a5d9d4d99431cbea4a3c3c82064218f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="b40f2-102">Método IHostThreadPoolManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="b40f2-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="b40f2-103">Obtém o número mínimo de threads ociosos que mantém o host no pool de threads em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="b40f2-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b40f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b40f2-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b40f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b40f2-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="b40f2-106">[out] Um ponteiro para o número mínimo de threads de trabalho ocioso que o host mantém no momento.</span><span class="sxs-lookup"><span data-stu-id="b40f2-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b40f2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b40f2-107">Return Value</span></span>  
  
|<span data-ttu-id="b40f2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b40f2-108">HRESULT</span></span>|<span data-ttu-id="b40f2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b40f2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b40f2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b40f2-110">S_OK</span></span>|<span data-ttu-id="b40f2-111">`GetMinThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b40f2-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b40f2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b40f2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b40f2-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b40f2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b40f2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b40f2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b40f2-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b40f2-115">The call timed out.</span></span>|  
|<span data-ttu-id="b40f2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b40f2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b40f2-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b40f2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b40f2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b40f2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b40f2-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b40f2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b40f2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b40f2-120">E_FAIL</span></span>|<span data-ttu-id="b40f2-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b40f2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b40f2-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b40f2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b40f2-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b40f2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b40f2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b40f2-124">E_NOTIMPL</span></span>|<span data-ttu-id="b40f2-125">O host não fornece uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="b40f2-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b40f2-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b40f2-126">Remarks</span></span>  
 <span data-ttu-id="b40f2-127">O host não é necessário fornecer uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="b40f2-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="b40f2-128">Nesse caso, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b40f2-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b40f2-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b40f2-129">Requirements</span></span>  
 <span data-ttu-id="b40f2-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b40f2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b40f2-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b40f2-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b40f2-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b40f2-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b40f2-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b40f2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40f2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b40f2-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="b40f2-135">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="b40f2-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="b40f2-136">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="b40f2-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="b40f2-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="b40f2-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
