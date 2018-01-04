---
title: "Método IHostSyncManager::SetCLRSyncManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.SetCLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fca59f0d2617c6fb244b2b1ed7b5cf46a7d5869f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="7d8ea-102">Método IHostSyncManager::SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7d8ea-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="7d8ea-103">Conjuntos de [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instância para associar atual [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d8ea-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d8ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7d8ea-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="7d8ea-106">[in] Um ponteiro para um `ICLRSyncManager` instância fornecida pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7d8ea-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d8ea-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7d8ea-107">Return Value</span></span>  
  
|<span data-ttu-id="7d8ea-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d8ea-108">HRESULT</span></span>|<span data-ttu-id="7d8ea-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d8ea-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d8ea-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d8ea-110">S_OK</span></span>|<span data-ttu-id="7d8ea-111">`SetCLRSyncManager`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="7d8ea-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d8ea-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d8ea-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d8ea-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d8ea-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d8ea-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-115">The call timed out.</span></span>|  
|<span data-ttu-id="7d8ea-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d8ea-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d8ea-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d8ea-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d8ea-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d8ea-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d8ea-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d8ea-120">E_FAIL</span></span>|<span data-ttu-id="7d8ea-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d8ea-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d8ea-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d8ea-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d8ea-124">Remarks</span></span>  
 <span data-ttu-id="7d8ea-125">Para facilitar a comunicação entre o host e o CLR, interfaces de hospedagem geralmente vêm em pares.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="7d8ea-126">Um membro do par é implementado pelo host e o outro membro é implementado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="7d8ea-127">Como uma implementação do host, o `IHostSyncManager` interface corresponde do `ICLRSyncManager` interface implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="7d8ea-128">O CLR chama `SetCLRSyncManager` para fornecer uma `ICLRSyncManager` instância do host associar atual `IHostSyncManager` instância.</span><span class="sxs-lookup"><span data-stu-id="7d8ea-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d8ea-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7d8ea-129">Requirements</span></span>  
 <span data-ttu-id="7d8ea-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d8ea-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d8ea-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d8ea-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d8ea-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7d8ea-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d8ea-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d8ea-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d8ea-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d8ea-134">See Also</span></span>  
 [<span data-ttu-id="7d8ea-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7d8ea-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="7d8ea-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="7d8ea-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
