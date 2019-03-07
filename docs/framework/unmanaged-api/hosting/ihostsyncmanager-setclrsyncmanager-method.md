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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27cf1ab377a3bb51700b287024d801e75107c8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57464915"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="c5ffc-102">Método IHostSyncManager::SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c5ffc-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="c5ffc-103">Define o [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instância a ser associado com o atual [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ffc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5ffc-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5ffc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5ffc-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="c5ffc-106">[in] Um ponteiro para um `ICLRSyncManager` instância fornecida pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c5ffc-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5ffc-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c5ffc-107">Return Value</span></span>  
  
|<span data-ttu-id="c5ffc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5ffc-108">HRESULT</span></span>|<span data-ttu-id="c5ffc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5ffc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5ffc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5ffc-110">S_OK</span></span>|<span data-ttu-id="c5ffc-111">`SetCLRSyncManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="c5ffc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5ffc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5ffc-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5ffc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5ffc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5ffc-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-115">The call timed out.</span></span>|  
|<span data-ttu-id="c5ffc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5ffc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5ffc-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5ffc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5ffc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5ffc-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5ffc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5ffc-120">E_FAIL</span></span>|<span data-ttu-id="c5ffc-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5ffc-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5ffc-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5ffc-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5ffc-124">Remarks</span></span>  
 <span data-ttu-id="c5ffc-125">Para facilitar a comunicação entre o host e o CLR, interfaces de hospedagem geralmente vêm em pares.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="c5ffc-126">Um membro do par é implementado pelo host, e outro membro é implementado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="c5ffc-127">Como uma implementação do lado do host, o `IHostSyncManager` interface corresponde à `ICLRSyncManager` interface implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="c5ffc-128">O CLR chama `SetCLRSyncManager` forneça um `ICLRSyncManager` instância do host associar atual `IHostSyncManager` instância.</span><span class="sxs-lookup"><span data-stu-id="c5ffc-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ffc-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5ffc-129">Requirements</span></span>  
 <span data-ttu-id="c5ffc-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5ffc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5ffc-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5ffc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5ffc-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c5ffc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5ffc-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5ffc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5ffc-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5ffc-134">See also</span></span>
- [<span data-ttu-id="c5ffc-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c5ffc-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c5ffc-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c5ffc-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
