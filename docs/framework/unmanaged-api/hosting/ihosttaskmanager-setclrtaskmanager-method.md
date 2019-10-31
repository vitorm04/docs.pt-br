---
title: Método IHostTaskManager::SetCLRTaskManager
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: c674cc43065bf8ea102bec1c5134757380454913
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141234"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="777e4-102">Método IHostTaskManager::SetCLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="777e4-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="777e4-103">Fornece ao host um ponteiro de interface para uma instância [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) implementada pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="777e4-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="777e4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="777e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="777e4-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="777e4-106">no Um ponteiro para uma instância `ICLRTaskManager` implementada pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="777e4-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="777e4-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="777e4-107">Return Value</span></span>  
  
|<span data-ttu-id="777e4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="777e4-108">HRESULT</span></span>|<span data-ttu-id="777e4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="777e4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="777e4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="777e4-110">S_OK</span></span>|<span data-ttu-id="777e4-111">`SetCLRTaskManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="777e4-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="777e4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="777e4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="777e4-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="777e4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="777e4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="777e4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="777e4-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="777e4-115">The call timed out.</span></span>|  
|<span data-ttu-id="777e4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="777e4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="777e4-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="777e4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="777e4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="777e4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="777e4-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="777e4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="777e4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="777e4-120">E_FAIL</span></span>|<span data-ttu-id="777e4-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="777e4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="777e4-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="777e4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="777e4-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="777e4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="777e4-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="777e4-124">Remarks</span></span>  
 <span data-ttu-id="777e4-125">O tempo de execução chama `SetCLRTaskManager` para fornecer ao host um ponteiro de interface para uma instância de `ICLRTaskManager`.</span><span class="sxs-lookup"><span data-stu-id="777e4-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="777e4-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="777e4-126">Requirements</span></span>  
 <span data-ttu-id="777e4-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="777e4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="777e4-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="777e4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="777e4-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="777e4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="777e4-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="777e4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777e4-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="777e4-131">See also</span></span>

- [<span data-ttu-id="777e4-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="777e4-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="777e4-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="777e4-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="777e4-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="777e4-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="777e4-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="777e4-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
