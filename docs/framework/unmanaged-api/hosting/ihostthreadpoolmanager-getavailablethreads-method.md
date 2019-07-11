---
title: Método IHostThreadPoolManager::GetAvailableThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a727a5287f6eaad600fc37befc32790fc4cf26
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749303"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="8231d-102">Método IHostThreadPoolManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="8231d-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="8231d-103">Obtém o número de threads no pool de threads que não estão processando no momento, os itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8231d-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8231d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8231d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8231d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8231d-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="8231d-106">[out] Ponteiro para o número de threads no pool de threads que não estão processando no momento, os itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8231d-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8231d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8231d-107">Return Value</span></span>  
  
|<span data-ttu-id="8231d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8231d-108">HRESULT</span></span>|<span data-ttu-id="8231d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8231d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8231d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8231d-110">S_OK</span></span>|<span data-ttu-id="8231d-111">`GetAvailableThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8231d-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8231d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8231d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8231d-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8231d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8231d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8231d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8231d-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8231d-115">The call timed out.</span></span>|  
|<span data-ttu-id="8231d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8231d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8231d-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8231d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8231d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8231d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8231d-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="8231d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8231d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8231d-120">E_FAIL</span></span>|<span data-ttu-id="8231d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8231d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8231d-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8231d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8231d-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8231d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8231d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8231d-124">E_NOTIMPL</span></span>|<span data-ttu-id="8231d-125">O host não fornece uma implementação de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="8231d-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8231d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="8231d-126">Remarks</span></span>  
 <span data-ttu-id="8231d-127">Se o host não fornecer uma implementação de `GetAvailableThreads`, ele deverá retornar um valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8231d-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8231d-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8231d-128">Requirements</span></span>  
 <span data-ttu-id="8231d-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8231d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8231d-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8231d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8231d-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8231d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8231d-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8231d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8231d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8231d-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="8231d-134">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="8231d-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
