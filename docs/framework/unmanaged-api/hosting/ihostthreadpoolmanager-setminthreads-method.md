---
title: "Método IHostThreadPoolManager::SetMinThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab0b107c050b1c4b686f761ede75ea2349825270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="23b50-102">Método IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="23b50-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="23b50-103">Define o número mínimo de threads ociosos que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="23b50-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23b50-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23b50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23b50-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="23b50-106">[in] O novo número mínimo de threads que o host deve manter.</span><span class="sxs-lookup"><span data-stu-id="23b50-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23b50-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="23b50-107">Return Value</span></span>  
  
|<span data-ttu-id="23b50-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23b50-108">HRESULT</span></span>|<span data-ttu-id="23b50-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="23b50-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23b50-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="23b50-110">S_OK</span></span>|<span data-ttu-id="23b50-111">`SetMinThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="23b50-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="23b50-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23b50-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23b50-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="23b50-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="23b50-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23b50-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="23b50-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="23b50-115">The call timed out.</span></span>|  
|<span data-ttu-id="23b50-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="23b50-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="23b50-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="23b50-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="23b50-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="23b50-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="23b50-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="23b50-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="23b50-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23b50-120">E_FAIL</span></span>|<span data-ttu-id="23b50-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="23b50-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="23b50-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="23b50-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="23b50-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="23b50-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="23b50-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="23b50-124">E_NOTIMPL</span></span>|<span data-ttu-id="23b50-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="23b50-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b50-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="23b50-126">Remarks</span></span>  
 <span data-ttu-id="23b50-127">Um host não é necessário fornecer uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="23b50-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="23b50-128">Nesse caso, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="23b50-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b50-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23b50-129">Requirements</span></span>  
 <span data-ttu-id="23b50-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23b50-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b50-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="23b50-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23b50-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="23b50-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23b50-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b50-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b50-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23b50-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="23b50-135">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="23b50-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="23b50-136">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="23b50-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="23b50-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="23b50-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
