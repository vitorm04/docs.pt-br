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
ms.openlocfilehash: 86bc320c28a5fbf122d234a4a1f15b674628c0b5
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803394"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="fc6da-102">Método IHostSyncManager::CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="fc6da-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="fc6da-103">Cria um objeto de seção crítica com contagem de rotação para sincronização.</span><span class="sxs-lookup"><span data-stu-id="fc6da-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc6da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc6da-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc6da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc6da-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="fc6da-106">no Especifica a contagem de rotação para o objeto de seção crítica.</span><span class="sxs-lookup"><span data-stu-id="fc6da-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="fc6da-107">fora Um ponteiro para o endereço de uma instância de [IHostCrst](ihostcrst-interface.md) ou NULL se a seção crítica não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="fc6da-107">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc6da-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="fc6da-108">Return Value</span></span>  
  
|<span data-ttu-id="fc6da-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc6da-109">HRESULT</span></span>|<span data-ttu-id="fc6da-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc6da-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc6da-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc6da-111">S_OK</span></span>|<span data-ttu-id="fc6da-112">`CreateCrstWithSpinCount`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="fc6da-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="fc6da-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc6da-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc6da-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="fc6da-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc6da-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc6da-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc6da-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fc6da-116">The call timed out.</span></span>|  
|<span data-ttu-id="fc6da-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc6da-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc6da-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="fc6da-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc6da-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc6da-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc6da-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="fc6da-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc6da-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc6da-121">E_FAIL</span></span>|<span data-ttu-id="fc6da-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fc6da-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc6da-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="fc6da-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc6da-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc6da-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fc6da-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fc6da-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fc6da-126">Não há memória suficiente disponível para criar a seção crítica solicitada.</span><span class="sxs-lookup"><span data-stu-id="fc6da-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc6da-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc6da-127">Remarks</span></span>  
 <span data-ttu-id="fc6da-128">Uma contagem de rotação é usada somente em um sistema com vários processadores.</span><span class="sxs-lookup"><span data-stu-id="fc6da-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="fc6da-129">A contagem de rotação especifica o número de vezes que um thread de chamada deve ser girado antes de executar uma operação de espera em um semáforo associado a uma seção crítica indisponível.</span><span class="sxs-lookup"><span data-stu-id="fc6da-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="fc6da-130">Se a seção crítica for liberada durante a operação de rotação, o thread de chamada evitará a operação de espera.</span><span class="sxs-lookup"><span data-stu-id="fc6da-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="fc6da-131">`CreateCrstWithSpinCount`espelha a função do Win32 `InitializeCriticalSectionAndSpinCount` .</span><span class="sxs-lookup"><span data-stu-id="fc6da-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc6da-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc6da-132">Requirements</span></span>  
 <span data-ttu-id="fc6da-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc6da-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc6da-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc6da-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc6da-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc6da-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc6da-136">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc6da-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc6da-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="fc6da-137">See also</span></span>

- [<span data-ttu-id="fc6da-138">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="fc6da-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="fc6da-139">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="fc6da-139">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="fc6da-140">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="fc6da-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
