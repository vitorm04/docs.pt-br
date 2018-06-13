---
title: Método IHostThreadPoolManager::SetMinThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f9852034f6d8208bdaa9b424f689adc374bae2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443668"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="ef794-102">Método IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="ef794-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="ef794-103">Define o número mínimo de threads ociosos que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="ef794-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef794-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef794-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef794-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef794-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="ef794-106">[in] O novo número mínimo de threads que o host deve manter.</span><span class="sxs-lookup"><span data-stu-id="ef794-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef794-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ef794-107">Return Value</span></span>  
  
|<span data-ttu-id="ef794-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef794-108">HRESULT</span></span>|<span data-ttu-id="ef794-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef794-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef794-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef794-110">S_OK</span></span>|<span data-ttu-id="ef794-111">`SetMinThreads` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ef794-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="ef794-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef794-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef794-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ef794-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef794-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef794-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef794-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="ef794-115">The call timed out.</span></span>|  
|<span data-ttu-id="ef794-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef794-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef794-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ef794-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef794-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef794-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef794-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="ef794-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef794-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef794-120">E_FAIL</span></span>|<span data-ttu-id="ef794-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ef794-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef794-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ef794-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef794-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ef794-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ef794-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ef794-124">E_NOTIMPL</span></span>|<span data-ttu-id="ef794-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="ef794-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef794-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef794-126">Remarks</span></span>  
 <span data-ttu-id="ef794-127">Um host não é necessário fornecer uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="ef794-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="ef794-128">Nesse caso, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ef794-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef794-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef794-129">Requirements</span></span>  
 <span data-ttu-id="ef794-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef794-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef794-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef794-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef794-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ef794-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef794-133">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef794-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef794-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef794-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="ef794-135">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="ef794-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="ef794-136">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="ef794-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="ef794-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="ef794-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
