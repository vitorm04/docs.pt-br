---
title: Método IHostSyncManager::CreateCrstWithSpinCount
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 451a5b163499b265396ae2e8f623b448e07ea807
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590910"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="77a52-102">Método IHostSyncManager::CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="77a52-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="77a52-103">Cria um objeto de seção crítica com contagem de rotação para a sincronização.</span><span class="sxs-lookup"><span data-stu-id="77a52-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77a52-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77a52-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77a52-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="77a52-106">[in] Especifica a contagem de rotação para o objeto de seção crítica.</span><span class="sxs-lookup"><span data-stu-id="77a52-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="77a52-107">[out] Um ponteiro para o endereço de um [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) da instância ou nulo se a seção crítica não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="77a52-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77a52-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="77a52-108">Return Value</span></span>  
  
|<span data-ttu-id="77a52-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77a52-109">HRESULT</span></span>|<span data-ttu-id="77a52-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="77a52-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77a52-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="77a52-111">S_OK</span></span>|<span data-ttu-id="77a52-112">`CreateCrstWithSpinCount` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="77a52-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="77a52-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77a52-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77a52-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="77a52-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77a52-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77a52-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77a52-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="77a52-116">The call timed out.</span></span>|  
|<span data-ttu-id="77a52-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77a52-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77a52-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="77a52-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77a52-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77a52-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77a52-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="77a52-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77a52-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77a52-121">E_FAIL</span></span>|<span data-ttu-id="77a52-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="77a52-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77a52-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="77a52-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77a52-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77a52-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="77a52-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="77a52-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="77a52-126">Não havia memória suficiente disponível para criar a seção crítica solicitada.</span><span class="sxs-lookup"><span data-stu-id="77a52-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77a52-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="77a52-127">Remarks</span></span>  
 <span data-ttu-id="77a52-128">Uma contagem de rotação é usada apenas em um sistema com vários processadores.</span><span class="sxs-lookup"><span data-stu-id="77a52-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="77a52-129">A contagem de rotações Especifica o número de vezes que um thread de chamada deve girar antes de executar uma operação de espera em um semáforo que está associado com uma seção crítica não está disponível.</span><span class="sxs-lookup"><span data-stu-id="77a52-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="77a52-130">Se a seção crítica ficar livre durante a operação de rotação, o thread de chamada evita a operação de espera.</span><span class="sxs-lookup"><span data-stu-id="77a52-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="77a52-131">`CreateCrstWithSpinCount` espelha o Win32 `InitializeCriticalSectionAndSpinCount` função.</span><span class="sxs-lookup"><span data-stu-id="77a52-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a52-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77a52-132">Requirements</span></span>  
 <span data-ttu-id="77a52-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77a52-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77a52-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77a52-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77a52-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="77a52-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77a52-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77a52-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a52-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77a52-137">See also</span></span>
- [<span data-ttu-id="77a52-138">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="77a52-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="77a52-139">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="77a52-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="77a52-140">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="77a52-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
