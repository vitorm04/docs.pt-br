---
title: "Método IHostPolicyManager::OnTimeout"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 272f78077c1d512fe574eebeaf6c92dc1939f6b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="e8f1a-102">Método IHostPolicyManager::OnTimeout</span><span class="sxs-lookup"><span data-stu-id="e8f1a-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="e8f1a-103">Notifica o host que o common language runtime (CLR) está prestes a realizar a ação especificada por uma chamada para o [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) método em resposta a um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8f1a-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8f1a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8f1a-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e8f1a-106">[in] Uma da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, que indica o tipo de operação atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="e8f1a-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação que o CLR está levando em resposta ao tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8f1a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e8f1a-108">Return Value</span></span>  
  
|<span data-ttu-id="e8f1a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8f1a-109">HRESULT</span></span>|<span data-ttu-id="e8f1a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8f1a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8f1a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8f1a-111">S_OK</span></span>|<span data-ttu-id="e8f1a-112">`OnTimeout`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="e8f1a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8f1a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8f1a-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8f1a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8f1a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8f1a-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-116">The call timed out.</span></span>|  
|<span data-ttu-id="e8f1a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8f1a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8f1a-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8f1a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8f1a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8f1a-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8f1a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8f1a-121">E_FAIL</span></span>|<span data-ttu-id="e8f1a-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8f1a-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8f1a-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8f1a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8f1a-125">Requirements</span></span>  
 <span data-ttu-id="e8f1a-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8f1a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f1a-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8f1a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8f1a-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e8f1a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8f1a-129">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f1a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f1a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8f1a-130">See Also</span></span>  
 [<span data-ttu-id="e8f1a-131">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="e8f1a-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="e8f1a-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="e8f1a-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="e8f1a-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e8f1a-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="e8f1a-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e8f1a-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
