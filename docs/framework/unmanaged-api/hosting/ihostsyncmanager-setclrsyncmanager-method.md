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
ms.openlocfilehash: 9c08a790d4dad748e5d09271bd870add22255b4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132621"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="dbc2f-102">Método IHostSyncManager::SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="dbc2f-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="dbc2f-103">Define a instância de [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) a ser associada à instância de [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbc2f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbc2f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbc2f-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="dbc2f-106">no Um ponteiro para uma instância de `ICLRSyncManager` fornecida pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbc2f-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dbc2f-107">Return Value</span></span>  
  
|<span data-ttu-id="dbc2f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbc2f-108">HRESULT</span></span>|<span data-ttu-id="dbc2f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbc2f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbc2f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbc2f-110">S_OK</span></span>|<span data-ttu-id="dbc2f-111">`SetCLRSyncManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="dbc2f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbc2f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbc2f-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbc2f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbc2f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbc2f-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-115">The call timed out.</span></span>|  
|<span data-ttu-id="dbc2f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbc2f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbc2f-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbc2f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbc2f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbc2f-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbc2f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbc2f-120">E_FAIL</span></span>|<span data-ttu-id="dbc2f-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbc2f-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbc2f-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbc2f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbc2f-124">Remarks</span></span>  
 <span data-ttu-id="dbc2f-125">Para facilitar a comunicação entre o host e o CLR, as interfaces de hospedagem geralmente vêm em pares.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="dbc2f-126">Um membro do par é implementado pelo host e o outro membro é implementado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="dbc2f-127">Como uma implementação do lado do host, a interface `IHostSyncManager` corresponde à interface `ICLRSyncManager` implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="dbc2f-128">O CLR chama `SetCLRSyncManager` para fornecer uma instância de `ICLRSyncManager` para que o host seja associado à instância de `IHostSyncManager` atual.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc2f-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbc2f-129">Requirements</span></span>  
 <span data-ttu-id="dbc2f-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc2f-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dbc2f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbc2f-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dbc2f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbc2f-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc2f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbc2f-134">See also</span></span>

- [<span data-ttu-id="dbc2f-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="dbc2f-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="dbc2f-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="dbc2f-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
