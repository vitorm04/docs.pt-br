---
title: Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a221b286ada97c3c03387556cb30ee6ddd2c453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="9adc5-102">Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="9adc5-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="9adc5-103">Modifica a política de associação para o assembly especificado e cria uma nova versão da política.</span><span class="sxs-lookup"><span data-stu-id="9adc5-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9adc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9adc5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9adc5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9adc5-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="9adc5-106">[in] A identidade do assembly para modificar.</span><span class="sxs-lookup"><span data-stu-id="9adc5-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="9adc5-107">[in] A nova identidade do assembly modificado.</span><span class="sxs-lookup"><span data-stu-id="9adc5-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="9adc5-108">[in] Um ponteiro para um buffer que contém os dados de política de associação para o assembly modificar.</span><span class="sxs-lookup"><span data-stu-id="9adc5-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="9adc5-109">[in] O tamanho da política de associação a ser substituído.</span><span class="sxs-lookup"><span data-stu-id="9adc5-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="9adc5-110">[in] Uma combinação de OR lógica de [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) valores, que indicam o controle de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="9adc5-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="9adc5-111">[out] Um ponteiro para um buffer que contém os novos dados de política de associação.</span><span class="sxs-lookup"><span data-stu-id="9adc5-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="9adc5-112">[out no] Um ponteiro para o tamanho do buffer de política de nova associação.</span><span class="sxs-lookup"><span data-stu-id="9adc5-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9adc5-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9adc5-113">Return Value</span></span>  
  
|<span data-ttu-id="9adc5-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9adc5-114">HRESULT</span></span>|<span data-ttu-id="9adc5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9adc5-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9adc5-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="9adc5-116">S_OK</span></span>|<span data-ttu-id="9adc5-117">A política foi modificada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9adc5-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="9adc5-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9adc5-118">E_INVALIDARG</span></span>|<span data-ttu-id="9adc5-119">`pwzSourceAssemblyIdentity` ou `pwzTargetAssemblyIdentity` era uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="9adc5-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="9adc5-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9adc5-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9adc5-121">`pbNewApplicationPolicy` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="9adc5-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="9adc5-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9adc5-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9adc5-123">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9adc5-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9adc5-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9adc5-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9adc5-125">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="9adc5-125">The call timed out.</span></span>|  
|<span data-ttu-id="9adc5-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9adc5-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9adc5-127">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9adc5-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9adc5-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9adc5-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9adc5-129">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="9adc5-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9adc5-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9adc5-130">E_FAIL</span></span>|<span data-ttu-id="9adc5-131">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9adc5-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9adc5-132">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="9adc5-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9adc5-133">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9adc5-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9adc5-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="9adc5-134">Remarks</span></span>  
 <span data-ttu-id="9adc5-135">O `ModifyApplicationPolicy` método pode ser chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="9adc5-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="9adc5-136">A primeira chamada deve fornecer um valor nulo para o `pbNewApplicationPolicy` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9adc5-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="9adc5-137">Essa chamada será retornada com o valor necessário para `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="9adc5-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="9adc5-138">A segunda chamada deve fornecer esse valor para `pcbNewAppPolicySize`e aponte para um buffer de tamanho para `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="9adc5-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9adc5-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9adc5-139">Requirements</span></span>  
 <span data-ttu-id="9adc5-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9adc5-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9adc5-141">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9adc5-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9adc5-142">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9adc5-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9adc5-143">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9adc5-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9adc5-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9adc5-144">See Also</span></span>  
 [<span data-ttu-id="9adc5-145">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="9adc5-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
