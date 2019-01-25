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
ms.openlocfilehash: 905ce9183d295568977eb7e216e5327d6b4ee8bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636086"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="dcb66-102">Método IHostThreadPoolManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="dcb66-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="dcb66-103">Define o número máximo de threads que o host pode manter no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="dcb66-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcb66-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcb66-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dcb66-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="dcb66-106">O número máximo de threads de trabalho no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="dcb66-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcb66-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dcb66-107">Return Value</span></span>  
  
|<span data-ttu-id="dcb66-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcb66-108">HRESULT</span></span>|<span data-ttu-id="dcb66-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dcb66-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcb66-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcb66-110">S_OK</span></span>|<span data-ttu-id="dcb66-111">`SetMaxThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dcb66-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="dcb66-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcb66-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcb66-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="dcb66-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcb66-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcb66-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcb66-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="dcb66-115">The call timed out.</span></span>|  
|<span data-ttu-id="dcb66-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcb66-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcb66-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="dcb66-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcb66-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcb66-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcb66-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="dcb66-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcb66-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcb66-120">E_FAIL</span></span>|<span data-ttu-id="dcb66-121">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dcb66-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="dcb66-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="dcb66-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcb66-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dcb66-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dcb66-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="dcb66-124">E_NOTIMPL</span></span>|<span data-ttu-id="dcb66-125">O host não fornece uma implementação de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="dcb66-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcb66-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="dcb66-126">Remarks</span></span>  
 <span data-ttu-id="dcb66-127">Um host não é necessário para permitir que o CLR configurar o tamanho do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="dcb66-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="dcb66-128">Alguns hosts poderá controle exclusivo sobre o pool de threads, por motivos como escalabilidade, desempenho ou implementação.</span><span class="sxs-lookup"><span data-stu-id="dcb66-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="dcb66-129">Nesse caso, um host deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="dcb66-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb66-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dcb66-130">Requirements</span></span>  
 <span data-ttu-id="dcb66-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcb66-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb66-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcb66-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcb66-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dcb66-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcb66-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb66-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb66-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcb66-135">See also</span></span>
- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="dcb66-136">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="dcb66-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="dcb66-137">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="dcb66-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="dcb66-138">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="dcb66-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
