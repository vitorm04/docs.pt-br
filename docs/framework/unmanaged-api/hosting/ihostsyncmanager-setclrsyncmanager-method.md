---
title: Método IHostSyncManager::SetCLRSyncManager
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: 7f1832b22a1b80855f48eba6d39bff64da6fa5f9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501437"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="963a1-102">Método IHostSyncManager::SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="963a1-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="963a1-103">Define a instância de [ICLRSyncManager](iclrsyncmanager-interface.md) a ser associada à instância de [IHostSyncManager](ihostsyncmanager-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="963a1-103">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="963a1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="963a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="963a1-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="963a1-106">no Um ponteiro para uma `ICLRSyncManager` instância fornecida pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="963a1-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="963a1-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="963a1-107">Return Value</span></span>  
  
|<span data-ttu-id="963a1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="963a1-108">HRESULT</span></span>|<span data-ttu-id="963a1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="963a1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="963a1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="963a1-110">S_OK</span></span>|<span data-ttu-id="963a1-111">`SetCLRSyncManager`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="963a1-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="963a1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="963a1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="963a1-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="963a1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="963a1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="963a1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="963a1-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="963a1-115">The call timed out.</span></span>|  
|<span data-ttu-id="963a1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="963a1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="963a1-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="963a1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="963a1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="963a1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="963a1-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="963a1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="963a1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="963a1-120">E_FAIL</span></span>|<span data-ttu-id="963a1-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="963a1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="963a1-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="963a1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="963a1-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="963a1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="963a1-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="963a1-124">Remarks</span></span>  
 <span data-ttu-id="963a1-125">Para facilitar a comunicação entre o host e o CLR, as interfaces de hospedagem geralmente vêm em pares.</span><span class="sxs-lookup"><span data-stu-id="963a1-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="963a1-126">Um membro do par é implementado pelo host e o outro membro é implementado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="963a1-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="963a1-127">Como uma implementação do lado do host, a `IHostSyncManager` interface corresponde à `ICLRSyncManager` interface implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="963a1-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="963a1-128">O CLR chama `SetCLRSyncManager` para fornecer uma `ICLRSyncManager` instância para que o host seja associado à `IHostSyncManager` instância atual.</span><span class="sxs-lookup"><span data-stu-id="963a1-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="963a1-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="963a1-129">Requirements</span></span>  
 <span data-ttu-id="963a1-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="963a1-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="963a1-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="963a1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="963a1-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="963a1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="963a1-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="963a1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963a1-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="963a1-134">See also</span></span>

- [<span data-ttu-id="963a1-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="963a1-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="963a1-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="963a1-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
