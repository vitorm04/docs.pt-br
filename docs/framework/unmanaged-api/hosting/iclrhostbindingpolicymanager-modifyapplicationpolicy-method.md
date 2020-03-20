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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178095"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="d44ff-102">Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="d44ff-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="d44ff-103">Modifica a política vinculativa para a montagem especificada e cria uma nova versão da política.</span><span class="sxs-lookup"><span data-stu-id="d44ff-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d44ff-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="d44ff-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d44ff-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="d44ff-106">[em] A identidade da assembléia para modificar.</span><span class="sxs-lookup"><span data-stu-id="d44ff-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="d44ff-107">[em] A nova identidade da montagem modificada.</span><span class="sxs-lookup"><span data-stu-id="d44ff-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="d44ff-108">[em] Um ponteiro para um buffer que contém os dados de diretiva de vinculação para a montagem modificar.</span><span class="sxs-lookup"><span data-stu-id="d44ff-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="d44ff-109">[em] O tamanho da política de vinculação a ser substituída.</span><span class="sxs-lookup"><span data-stu-id="d44ff-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="d44ff-110">[em] Uma combinação ou lógica de valores [EHostBindingPolicyModifyModifyFlags,](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) indicando o controle do redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d44ff-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="d44ff-111">[fora] Um ponteiro para um buffer que contém os novos dados de diretiva de vinculação.</span><span class="sxs-lookup"><span data-stu-id="d44ff-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="d44ff-112">[dentro, fora] Um ponteiro para o tamanho do novo buffer de diretiva de vinculação.</span><span class="sxs-lookup"><span data-stu-id="d44ff-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d44ff-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d44ff-113">Return Value</span></span>  
  
|<span data-ttu-id="d44ff-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d44ff-114">HRESULT</span></span>|<span data-ttu-id="d44ff-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d44ff-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d44ff-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="d44ff-116">S_OK</span></span>|<span data-ttu-id="d44ff-117">A política foi modificada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d44ff-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="d44ff-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d44ff-118">E_INVALIDARG</span></span>|<span data-ttu-id="d44ff-119">`pwzSourceAssemblyIdentity`ou `pwzTargetAssemblyIdentity` era uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="d44ff-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="d44ff-120">Error_insufficient_buffer</span><span class="sxs-lookup"><span data-stu-id="d44ff-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d44ff-121">`pbNewApplicationPolicy` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="d44ff-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="d44ff-122">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="d44ff-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d44ff-123">O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d44ff-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d44ff-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d44ff-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d44ff-125">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="d44ff-125">The call timed out.</span></span>|  
|<span data-ttu-id="d44ff-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d44ff-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d44ff-127">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="d44ff-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d44ff-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d44ff-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d44ff-129">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="d44ff-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d44ff-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d44ff-130">E_FAIL</span></span>|<span data-ttu-id="d44ff-131">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="d44ff-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d44ff-132">Depois que um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d44ff-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d44ff-133">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d44ff-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d44ff-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="d44ff-134">Remarks</span></span>  
 <span data-ttu-id="d44ff-135">O `ModifyApplicationPolicy` método pode ser chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="d44ff-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="d44ff-136">A primeira chamada deve fornecer `pbNewApplicationPolicy` um valor nulo para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d44ff-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="d44ff-137">Esta chamada retornará com `pcbNewAppPolicySize`o valor necessário para .</span><span class="sxs-lookup"><span data-stu-id="d44ff-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="d44ff-138">A segunda chamada deve `pcbNewAppPolicySize`fornecer esse valor para , `pbNewApplicationPolicy`e apontar para um buffer desse tamanho para .</span><span class="sxs-lookup"><span data-stu-id="d44ff-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44ff-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d44ff-139">Requirements</span></span>  
 <span data-ttu-id="d44ff-140">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44ff-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d44ff-141">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d44ff-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d44ff-142">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d44ff-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d44ff-143">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d44ff-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44ff-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="d44ff-144">See also</span></span>

- [<span data-ttu-id="d44ff-145">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="d44ff-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
