---
title: "Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51775f52e34f35d8ef9f3a8533363be73e9bd7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="a02ea-102">Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="a02ea-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="a02ea-103">Modifica a política de associação para o assembly especificado e cria uma nova versão da política.</span><span class="sxs-lookup"><span data-stu-id="a02ea-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a02ea-104">Syntax</span></span>  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a02ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a02ea-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="a02ea-106">[in] A identidade do assembly para modificar.</span><span class="sxs-lookup"><span data-stu-id="a02ea-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="a02ea-107">[in] A nova identidade do assembly modificado.</span><span class="sxs-lookup"><span data-stu-id="a02ea-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="a02ea-108">[in] Um ponteiro para um buffer que contém os dados de política de associação para o assembly modificar.</span><span class="sxs-lookup"><span data-stu-id="a02ea-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="a02ea-109">[in] O tamanho da política de associação a ser substituído.</span><span class="sxs-lookup"><span data-stu-id="a02ea-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="a02ea-110">[in] Uma combinação de OR lógica de [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) valores, que indicam o controle de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="a02ea-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="a02ea-111">[out] Um ponteiro para um buffer que contém os novos dados de política de associação.</span><span class="sxs-lookup"><span data-stu-id="a02ea-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="a02ea-112">[out no] Um ponteiro para o tamanho do buffer de política de nova associação.</span><span class="sxs-lookup"><span data-stu-id="a02ea-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a02ea-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a02ea-113">Return Value</span></span>  
  
|<span data-ttu-id="a02ea-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a02ea-114">HRESULT</span></span>|<span data-ttu-id="a02ea-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a02ea-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a02ea-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a02ea-116">S_OK</span></span>|<span data-ttu-id="a02ea-117">A política foi modificada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a02ea-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="a02ea-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a02ea-118">E_INVALIDARG</span></span>|<span data-ttu-id="a02ea-119">`pwzSourceAssemblyIdentity`ou `pwzTargetAssemblyIdentity` era uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="a02ea-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="a02ea-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a02ea-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a02ea-121">`pbNewApplicationPolicy` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="a02ea-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="a02ea-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a02ea-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a02ea-123">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a02ea-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a02ea-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a02ea-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a02ea-125">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="a02ea-125">The call timed out.</span></span>|  
|<span data-ttu-id="a02ea-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a02ea-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a02ea-127">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a02ea-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a02ea-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a02ea-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a02ea-129">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="a02ea-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a02ea-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a02ea-130">E_FAIL</span></span>|<span data-ttu-id="a02ea-131">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a02ea-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a02ea-132">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a02ea-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a02ea-133">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a02ea-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a02ea-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="a02ea-134">Remarks</span></span>  
 <span data-ttu-id="a02ea-135">O `ModifyApplicationPolicy` método pode ser chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="a02ea-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="a02ea-136">A primeira chamada deve fornecer um valor nulo para o `pbNewApplicationPolicy` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a02ea-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="a02ea-137">Essa chamada será retornada com o valor necessário para `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="a02ea-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="a02ea-138">A segunda chamada deve fornecer esse valor para `pcbNewAppPolicySize`e aponte para um buffer de tamanho para `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="a02ea-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a02ea-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a02ea-139">Requirements</span></span>  
 <span data-ttu-id="a02ea-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a02ea-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02ea-141">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a02ea-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a02ea-142">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a02ea-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a02ea-143">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02ea-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02ea-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a02ea-144">See Also</span></span>  
 [<span data-ttu-id="a02ea-145">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="a02ea-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
