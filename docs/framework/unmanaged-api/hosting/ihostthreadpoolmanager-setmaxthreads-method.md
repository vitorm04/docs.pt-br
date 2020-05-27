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
ms.openlocfilehash: 53d42afda6668acc6462c419fcefd6bc1435a34c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842446"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="e7c80-102">Método IHostThreadPoolManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="e7c80-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="e7c80-103">Define o número máximo de threads que o host pode manter no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="e7c80-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7c80-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7c80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7c80-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="e7c80-106">O número máximo de threads de trabalho no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="e7c80-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7c80-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="e7c80-107">Return Value</span></span>  
  
|<span data-ttu-id="e7c80-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7c80-108">HRESULT</span></span>|<span data-ttu-id="e7c80-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7c80-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7c80-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7c80-110">S_OK</span></span>|<span data-ttu-id="e7c80-111">`SetMaxThreads`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e7c80-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e7c80-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7c80-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7c80-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e7c80-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7c80-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7c80-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7c80-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e7c80-115">The call timed out.</span></span>|  
|<span data-ttu-id="e7c80-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7c80-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7c80-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e7c80-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7c80-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7c80-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7c80-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e7c80-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7c80-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e7c80-120">E_FAIL</span></span>|<span data-ttu-id="e7c80-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e7c80-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e7c80-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e7c80-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7c80-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e7c80-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e7c80-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e7c80-124">E_NOTIMPL</span></span>|<span data-ttu-id="e7c80-125">O host não fornece uma implementação de `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="e7c80-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7c80-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7c80-126">Remarks</span></span>  
 <span data-ttu-id="e7c80-127">Não é necessário um host para permitir que o CLR configure o tamanho do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="e7c80-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="e7c80-128">Alguns hosts podem querer um controle exclusivo sobre o pool de threads, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="e7c80-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e7c80-129">Nesse caso, um host deve retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="e7c80-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7c80-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7c80-130">Requirements</span></span>  
 <span data-ttu-id="e7c80-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7c80-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7c80-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e7c80-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7c80-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e7c80-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7c80-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7c80-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c80-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7c80-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="e7c80-136">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="e7c80-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="e7c80-137">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="e7c80-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="e7c80-138">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="e7c80-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
