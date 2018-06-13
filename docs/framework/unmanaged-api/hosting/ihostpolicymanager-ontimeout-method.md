---
title: Método IHostPolicyManager::OnTimeout
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f6257cdf966850a17d5cf58ef1ac2e6ab7103b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439368"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="10fbb-102">Método IHostPolicyManager::OnTimeout</span><span class="sxs-lookup"><span data-stu-id="10fbb-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="10fbb-103">Notifica o host que o common language runtime (CLR) está prestes a realizar a ação especificada por uma chamada para o [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) método em resposta a um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="10fbb-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10fbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10fbb-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10fbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10fbb-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="10fbb-106">[in] Uma da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, que indica o tipo de operação atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="10fbb-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="10fbb-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação que o CLR está levando em resposta ao tempo limite.</span><span class="sxs-lookup"><span data-stu-id="10fbb-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10fbb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="10fbb-108">Return Value</span></span>  
  
|<span data-ttu-id="10fbb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10fbb-109">HRESULT</span></span>|<span data-ttu-id="10fbb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fbb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10fbb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="10fbb-111">S_OK</span></span>|<span data-ttu-id="10fbb-112">`OnTimeout` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="10fbb-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="10fbb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10fbb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10fbb-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="10fbb-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10fbb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10fbb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10fbb-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="10fbb-116">The call timed out.</span></span>|  
|<span data-ttu-id="10fbb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10fbb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10fbb-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="10fbb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10fbb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10fbb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10fbb-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="10fbb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10fbb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10fbb-121">E_FAIL</span></span>|<span data-ttu-id="10fbb-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="10fbb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10fbb-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="10fbb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10fbb-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10fbb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10fbb-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10fbb-125">Requirements</span></span>  
 <span data-ttu-id="10fbb-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10fbb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10fbb-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10fbb-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10fbb-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="10fbb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10fbb-129">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10fbb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10fbb-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10fbb-130">See Also</span></span>  
 [<span data-ttu-id="10fbb-131">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="10fbb-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="10fbb-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="10fbb-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="10fbb-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="10fbb-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="10fbb-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="10fbb-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
