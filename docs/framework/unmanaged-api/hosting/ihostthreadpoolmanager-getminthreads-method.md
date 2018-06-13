---
title: Método IHostThreadPoolManager::GetMinThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2064f134d83e6d410e851d8ea9498b45e36aea37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442261"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="3a890-102">Método IHostThreadPoolManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="3a890-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="3a890-103">Obtém o número mínimo de threads ociosos que mantém o host no pool de threads em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="3a890-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a890-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a890-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a890-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a890-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="3a890-106">[out] Um ponteiro para o número mínimo de threads de trabalho ocioso que o host mantém no momento.</span><span class="sxs-lookup"><span data-stu-id="3a890-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a890-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3a890-107">Return Value</span></span>  
  
|<span data-ttu-id="3a890-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a890-108">HRESULT</span></span>|<span data-ttu-id="3a890-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a890-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a890-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a890-110">S_OK</span></span>|<span data-ttu-id="3a890-111">`GetMinThreads` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="3a890-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="3a890-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a890-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a890-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3a890-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a890-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a890-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a890-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="3a890-115">The call timed out.</span></span>|  
|<span data-ttu-id="3a890-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a890-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a890-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3a890-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a890-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a890-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a890-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="3a890-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a890-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a890-120">E_FAIL</span></span>|<span data-ttu-id="3a890-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3a890-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a890-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3a890-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a890-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3a890-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3a890-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3a890-124">E_NOTIMPL</span></span>|<span data-ttu-id="3a890-125">O host não fornece uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="3a890-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a890-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a890-126">Remarks</span></span>  
 <span data-ttu-id="3a890-127">O host não é necessário fornecer uma implementação de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="3a890-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="3a890-128">Nesse caso, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3a890-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a890-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a890-129">Requirements</span></span>  
 <span data-ttu-id="3a890-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a890-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a890-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a890-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a890-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3a890-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a890-133">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a890-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a890-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a890-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="3a890-135">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="3a890-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="3a890-136">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="3a890-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="3a890-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="3a890-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
