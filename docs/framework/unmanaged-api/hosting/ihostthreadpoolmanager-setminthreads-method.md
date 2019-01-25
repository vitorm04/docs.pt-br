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
ms.openlocfilehash: 7d0e8198fece4a718b6478f199820738d49ed988
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519834"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="d1564-102">Método IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="d1564-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="d1564-103">Define o número mínimo de threads ociosos do que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="d1564-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1564-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1564-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1564-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1564-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="d1564-106">[in] O novo número mínimo de threads que o host deve manter.</span><span class="sxs-lookup"><span data-stu-id="d1564-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1564-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d1564-107">Return Value</span></span>  
  
|<span data-ttu-id="d1564-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1564-108">HRESULT</span></span>|<span data-ttu-id="d1564-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1564-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1564-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1564-110">S_OK</span></span>|<span data-ttu-id="d1564-111">`SetMinThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d1564-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d1564-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1564-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1564-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d1564-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1564-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1564-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1564-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d1564-115">The call timed out.</span></span>|  
|<span data-ttu-id="d1564-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1564-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1564-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d1564-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1564-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1564-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1564-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="d1564-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1564-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1564-120">E_FAIL</span></span>|<span data-ttu-id="d1564-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d1564-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1564-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d1564-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1564-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d1564-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d1564-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d1564-124">E_NOTIMPL</span></span>|<span data-ttu-id="d1564-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="d1564-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1564-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1564-126">Remarks</span></span>  
 <span data-ttu-id="d1564-127">Um host não é necessário para fornecer uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="d1564-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="d1564-128">Nesse caso, ele deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d1564-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1564-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1564-129">Requirements</span></span>  
 <span data-ttu-id="d1564-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1564-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1564-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1564-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1564-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d1564-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1564-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1564-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1564-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1564-134">See also</span></span>
- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="d1564-135">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="d1564-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="d1564-136">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d1564-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="d1564-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="d1564-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
