---
title: "Método IHostTaskManager::SetCLRTaskManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetCLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ec0d515ad4c0bc21e1036f20f17bf168d7af79d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="be8da-102">Método IHostTaskManager::SetCLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="be8da-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="be8da-103">Fornece o host com um ponteiro de interface para um [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instância implementada pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="be8da-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be8da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be8da-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be8da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="be8da-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="be8da-106">[in] Um ponteiro para um `ICLRTaskManager` instância implementada pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="be8da-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be8da-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="be8da-107">Return Value</span></span>  
  
|<span data-ttu-id="be8da-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be8da-108">HRESULT</span></span>|<span data-ttu-id="be8da-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="be8da-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be8da-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="be8da-110">S_OK</span></span>|<span data-ttu-id="be8da-111">`SetCLRTaskManager`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="be8da-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="be8da-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be8da-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be8da-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="be8da-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be8da-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be8da-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be8da-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="be8da-115">The call timed out.</span></span>|  
|<span data-ttu-id="be8da-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be8da-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be8da-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="be8da-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be8da-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be8da-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be8da-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="be8da-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be8da-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be8da-120">E_FAIL</span></span>|<span data-ttu-id="be8da-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="be8da-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be8da-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="be8da-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be8da-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="be8da-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be8da-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="be8da-124">Remarks</span></span>  
 <span data-ttu-id="be8da-125">O tempo de execução chama `SetCLRTaskManager` para fornecer o host com um ponteiro de interface para um `ICLRTaskManager` instância.</span><span class="sxs-lookup"><span data-stu-id="be8da-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be8da-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be8da-126">Requirements</span></span>  
 <span data-ttu-id="be8da-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be8da-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be8da-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be8da-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be8da-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="be8da-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be8da-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be8da-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be8da-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be8da-131">See Also</span></span>  
 [<span data-ttu-id="be8da-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="be8da-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="be8da-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="be8da-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="be8da-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="be8da-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="be8da-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="be8da-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
