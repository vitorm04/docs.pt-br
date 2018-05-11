---
title: Método IHostPolicyManager::OnFailure
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87b4d4a9606723e5cf55fac19469809e1014b7c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="74899-102">Método IHostPolicyManager::OnFailure</span><span class="sxs-lookup"><span data-stu-id="74899-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="74899-103">Notifica o host que o common language runtime (CLR) está prestes a realizar a ação especificada por uma chamada para o [SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) método em resposta a uma falha de alocação ou recuperação de recursos.</span><span class="sxs-lookup"><span data-stu-id="74899-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74899-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74899-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74899-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74899-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="74899-106">[in] Uma da [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores, que indica o tipo de falha para o qual o CLR está respondendo.</span><span class="sxs-lookup"><span data-stu-id="74899-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="74899-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação que o CLR é executada em resposta ao `failure`.</span><span class="sxs-lookup"><span data-stu-id="74899-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74899-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="74899-108">Return Value</span></span>  
  
|<span data-ttu-id="74899-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74899-109">HRESULT</span></span>|<span data-ttu-id="74899-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="74899-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74899-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="74899-111">S_OK</span></span>|<span data-ttu-id="74899-112">`OnFailure` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="74899-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="74899-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74899-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74899-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="74899-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74899-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74899-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74899-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="74899-116">The call timed out.</span></span>|  
|<span data-ttu-id="74899-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74899-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74899-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="74899-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74899-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74899-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74899-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="74899-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74899-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74899-121">E_FAIL</span></span>|<span data-ttu-id="74899-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="74899-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74899-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="74899-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74899-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74899-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74899-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74899-125">Requirements</span></span>  
 <span data-ttu-id="74899-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74899-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74899-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74899-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74899-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="74899-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74899-129">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74899-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74899-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74899-130">See Also</span></span>  
 [<span data-ttu-id="74899-131">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="74899-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="74899-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="74899-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="74899-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="74899-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="74899-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="74899-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
