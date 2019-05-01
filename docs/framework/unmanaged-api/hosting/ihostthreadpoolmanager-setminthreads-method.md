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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046209"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="4159d-102">Método IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="4159d-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="4159d-103">Define o número mínimo de threads ociosos do que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="4159d-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4159d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4159d-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4159d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4159d-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="4159d-106">[in] O novo número mínimo de threads que o host deve manter.</span><span class="sxs-lookup"><span data-stu-id="4159d-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4159d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4159d-107">Return Value</span></span>  
  
|<span data-ttu-id="4159d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4159d-108">HRESULT</span></span>|<span data-ttu-id="4159d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4159d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4159d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4159d-110">S_OK</span></span>|<span data-ttu-id="4159d-111">`SetMinThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4159d-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4159d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4159d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4159d-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4159d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4159d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4159d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4159d-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4159d-115">The call timed out.</span></span>|  
|<span data-ttu-id="4159d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4159d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4159d-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4159d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4159d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4159d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4159d-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="4159d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4159d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4159d-120">E_FAIL</span></span>|<span data-ttu-id="4159d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4159d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4159d-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4159d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4159d-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4159d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4159d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4159d-124">E_NOTIMPL</span></span>|<span data-ttu-id="4159d-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4159d-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4159d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4159d-126">Remarks</span></span>  
 <span data-ttu-id="4159d-127">Um host não é necessário para fornecer uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4159d-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="4159d-128">Nesse caso, ele deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4159d-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4159d-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4159d-129">Requirements</span></span>  
 <span data-ttu-id="4159d-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4159d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4159d-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4159d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4159d-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4159d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4159d-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4159d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4159d-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4159d-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4159d-135">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="4159d-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="4159d-136">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="4159d-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="4159d-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="4159d-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
