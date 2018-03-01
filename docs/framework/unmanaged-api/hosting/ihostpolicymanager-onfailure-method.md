---
title: "Método IHostPolicyManager::OnFailure"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e3cd6c095ff5736e7491648cc3aca35fb2319c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="704ec-102">Método IHostPolicyManager::OnFailure</span><span class="sxs-lookup"><span data-stu-id="704ec-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="704ec-103">Notifica o host que o common language runtime (CLR) está prestes a realizar a ação especificada por uma chamada para o [SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) método em resposta a uma falha de alocação ou recuperação de recursos.</span><span class="sxs-lookup"><span data-stu-id="704ec-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="704ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="704ec-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="704ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="704ec-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="704ec-106">[in] Uma da [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores, que indica o tipo de falha para o qual o CLR está respondendo.</span><span class="sxs-lookup"><span data-stu-id="704ec-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="704ec-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação que o CLR é executada em resposta ao `failure`.</span><span class="sxs-lookup"><span data-stu-id="704ec-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="704ec-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="704ec-108">Return Value</span></span>  
  
|<span data-ttu-id="704ec-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="704ec-109">HRESULT</span></span>|<span data-ttu-id="704ec-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="704ec-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="704ec-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="704ec-111">S_OK</span></span>|<span data-ttu-id="704ec-112">`OnFailure`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="704ec-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="704ec-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="704ec-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="704ec-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="704ec-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="704ec-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="704ec-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="704ec-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="704ec-116">The call timed out.</span></span>|  
|<span data-ttu-id="704ec-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="704ec-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="704ec-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="704ec-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="704ec-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="704ec-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="704ec-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="704ec-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="704ec-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="704ec-121">E_FAIL</span></span>|<span data-ttu-id="704ec-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="704ec-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="704ec-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="704ec-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="704ec-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="704ec-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="704ec-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="704ec-125">Requirements</span></span>  
 <span data-ttu-id="704ec-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="704ec-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="704ec-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="704ec-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="704ec-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="704ec-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="704ec-129">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="704ec-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704ec-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="704ec-130">See Also</span></span>  
 [<span data-ttu-id="704ec-131">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="704ec-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="704ec-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="704ec-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="704ec-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="704ec-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="704ec-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="704ec-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
