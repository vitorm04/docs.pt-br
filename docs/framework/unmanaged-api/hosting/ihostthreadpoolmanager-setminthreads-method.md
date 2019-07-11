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
ms.openlocfilehash: 3c79f18c1deec4183a5a736c5acf88e9a1fd8021
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749099"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="f231e-102">Método IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="f231e-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="f231e-103">Define o número mínimo de threads ociosos do que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="f231e-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f231e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f231e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f231e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f231e-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="f231e-106">[in] O novo número mínimo de threads que o host deve manter.</span><span class="sxs-lookup"><span data-stu-id="f231e-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f231e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f231e-107">Return Value</span></span>  
  
|<span data-ttu-id="f231e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f231e-108">HRESULT</span></span>|<span data-ttu-id="f231e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f231e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f231e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f231e-110">S_OK</span></span>|<span data-ttu-id="f231e-111">`SetMinThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f231e-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f231e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f231e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f231e-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f231e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f231e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f231e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f231e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f231e-115">The call timed out.</span></span>|  
|<span data-ttu-id="f231e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f231e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f231e-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f231e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f231e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f231e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f231e-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="f231e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f231e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f231e-120">E_FAIL</span></span>|<span data-ttu-id="f231e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f231e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f231e-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f231e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f231e-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f231e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f231e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f231e-124">E_NOTIMPL</span></span>|<span data-ttu-id="f231e-125">O host não fornece uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="f231e-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f231e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="f231e-126">Remarks</span></span>  
 <span data-ttu-id="f231e-127">Um host não é necessário para fornecer uma implementação de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="f231e-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="f231e-128">Nesse caso, ele deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f231e-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f231e-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f231e-129">Requirements</span></span>  
 <span data-ttu-id="f231e-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f231e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f231e-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f231e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f231e-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f231e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f231e-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f231e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f231e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f231e-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="f231e-135">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="f231e-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="f231e-136">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="f231e-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="f231e-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="f231e-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
