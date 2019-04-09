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
ms.openlocfilehash: 78d2b84598a034bf6c534745bcb99a080d039617
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100321"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="3c1f9-102">Método IHostPolicyManager::OnFailure</span><span class="sxs-lookup"><span data-stu-id="3c1f9-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="3c1f9-103">Notifica o host que o common language runtime (CLR) está prestes a realizar a ação especificada por uma chamada para o [ICLRPolicyManager:: SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) método em resposta a uma falha de alocação ou recuperação de recursos.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c1f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c1f9-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c1f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c1f9-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="3c1f9-106">[in] Um dos [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores, que indica o tipo de falha para o qual o CLR está respondendo.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="3c1f9-107">[in] Um dos [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação que o CLR é executada em resposta ao `failure`.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c1f9-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3c1f9-108">Return Value</span></span>  
  
|<span data-ttu-id="3c1f9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c1f9-109">HRESULT</span></span>|<span data-ttu-id="3c1f9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c1f9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c1f9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c1f9-111">S_OK</span></span>|`OnFailure` <span data-ttu-id="3c1f9-112">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-112">returned successfully.</span></span>|  
|<span data-ttu-id="3c1f9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c1f9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c1f9-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3c1f9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c1f9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c1f9-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-116">The call timed out.</span></span>|  
|<span data-ttu-id="3c1f9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c1f9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c1f9-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c1f9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c1f9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c1f9-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c1f9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c1f9-121">E_FAIL</span></span>|<span data-ttu-id="3c1f9-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c1f9-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c1f9-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3c1f9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c1f9-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c1f9-125">Requirements</span></span>  
 <span data-ttu-id="3c1f9-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c1f9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c1f9-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c1f9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c1f9-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3c1f9-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3c1f9-129">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3c1f9-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3c1f9-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c1f9-130">See also</span></span>

- [<span data-ttu-id="3c1f9-131">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="3c1f9-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="3c1f9-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="3c1f9-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="3c1f9-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="3c1f9-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="3c1f9-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="3c1f9-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
