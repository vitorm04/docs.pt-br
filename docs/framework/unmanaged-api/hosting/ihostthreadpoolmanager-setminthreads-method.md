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
ms.openlocfilehash: e290f20feacc59944bb1cafded327f4316ab88d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174155"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="e78a2-102">Método IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="e78a2-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="e78a2-103">Define o número mínimo de threads ociosos do que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="e78a2-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e78a2-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e78a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e78a2-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="e78a2-106">[in] O novo número mínimo de threads que o host deve manter.</span><span class="sxs-lookup"><span data-stu-id="e78a2-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e78a2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e78a2-107">Return Value</span></span>  
  
|<span data-ttu-id="e78a2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e78a2-108">HRESULT</span></span>|<span data-ttu-id="e78a2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e78a2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e78a2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e78a2-110">S_OK</span></span>|`SetMinThreads` <span data-ttu-id="e78a2-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e78a2-111">returned successfully.</span></span>|  
|<span data-ttu-id="e78a2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e78a2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e78a2-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e78a2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e78a2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e78a2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e78a2-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e78a2-115">The call timed out.</span></span>|  
|<span data-ttu-id="e78a2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e78a2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e78a2-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e78a2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e78a2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e78a2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e78a2-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e78a2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e78a2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e78a2-120">E_FAIL</span></span>|<span data-ttu-id="e78a2-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e78a2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e78a2-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e78a2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e78a2-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e78a2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e78a2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e78a2-124">E_NOTIMPL</span></span>|<span data-ttu-id="e78a2-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="e78a2-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e78a2-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e78a2-126">Remarks</span></span>  
 <span data-ttu-id="e78a2-127">Um host não é necessário para fornecer uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="e78a2-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="e78a2-128">Nesse caso, ele deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="e78a2-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e78a2-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e78a2-129">Requirements</span></span>  
 <span data-ttu-id="e78a2-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e78a2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e78a2-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e78a2-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e78a2-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e78a2-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e78a2-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e78a2-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e78a2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e78a2-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="e78a2-135">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="e78a2-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="e78a2-136">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="e78a2-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="e78a2-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="e78a2-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
