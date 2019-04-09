---
title: Método IHostThreadPoolManager::SetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0df8d11bba870dfec880401064ec3f78f5f04e1f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081470"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="8a796-102">Método IHostThreadPoolManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="8a796-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="8a796-103">Define o número máximo de threads que o host pode manter no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="8a796-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a796-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a796-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a796-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a796-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="8a796-106">O número máximo de threads de trabalho no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="8a796-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a796-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8a796-107">Return Value</span></span>  
  
|<span data-ttu-id="8a796-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a796-108">HRESULT</span></span>|<span data-ttu-id="8a796-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a796-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a796-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a796-110">S_OK</span></span>|`SetMaxThreads` <span data-ttu-id="8a796-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8a796-111">returned successfully.</span></span>|  
|<span data-ttu-id="8a796-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8a796-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8a796-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8a796-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8a796-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8a796-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8a796-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8a796-115">The call timed out.</span></span>|  
|<span data-ttu-id="8a796-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a796-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8a796-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8a796-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8a796-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8a796-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8a796-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="8a796-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8a796-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a796-120">E_FAIL</span></span>|<span data-ttu-id="8a796-121">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8a796-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8a796-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8a796-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8a796-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8a796-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8a796-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8a796-124">E_NOTIMPL</span></span>|<span data-ttu-id="8a796-125">O host não fornece uma implementação de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="8a796-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a796-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a796-126">Remarks</span></span>  
 <span data-ttu-id="8a796-127">Um host não é necessário para permitir que o CLR configurar o tamanho do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="8a796-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="8a796-128">Alguns hosts poderá controle exclusivo sobre o pool de threads, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="8a796-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="8a796-129">Nesse caso, um host deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8a796-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a796-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a796-130">Requirements</span></span>  
 <span data-ttu-id="8a796-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a796-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a796-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a796-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a796-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8a796-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8a796-134">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8a796-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a796-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a796-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="8a796-136">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="8a796-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="8a796-137">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="8a796-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="8a796-138">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="8a796-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
