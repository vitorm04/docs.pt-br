---
title: "Método IHostThreadPoolManager::GetMinThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8ee8adfb93a3e098bb6df69ad00202118bc1731e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="b9810-102">Método IHostThreadPoolManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="b9810-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="b9810-103">Obtém o número mínimo de threads ociosos que mantém o host no pool de threads em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="b9810-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9810-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9810-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9810-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9810-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="b9810-106">[out] Um ponteiro para o número mínimo de threads de trabalho ocioso que o host mantém no momento.</span><span class="sxs-lookup"><span data-stu-id="b9810-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9810-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b9810-107">Return Value</span></span>  
  
|<span data-ttu-id="b9810-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9810-108">HRESULT</span></span>|<span data-ttu-id="b9810-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9810-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9810-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9810-110">S_OK</span></span>|<span data-ttu-id="b9810-111">`GetMinThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b9810-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b9810-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9810-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9810-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b9810-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9810-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9810-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9810-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b9810-115">The call timed out.</span></span>|  
|<span data-ttu-id="b9810-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9810-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9810-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b9810-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9810-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9810-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9810-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b9810-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9810-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9810-120">E_FAIL</span></span>|<span data-ttu-id="b9810-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b9810-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9810-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b9810-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9810-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9810-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b9810-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b9810-124">E_NOTIMPL</span></span>|<span data-ttu-id="b9810-125">O host não fornece uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="b9810-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9810-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9810-126">Remarks</span></span>  
 <span data-ttu-id="b9810-127">O host não é necessário fornecer uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="b9810-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="b9810-128">Nesse caso, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b9810-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9810-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9810-129">Requirements</span></span>  
 <span data-ttu-id="b9810-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9810-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9810-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b9810-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9810-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b9810-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9810-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9810-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9810-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9810-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="b9810-135">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="b9810-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="b9810-136">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="b9810-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="b9810-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="b9810-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
