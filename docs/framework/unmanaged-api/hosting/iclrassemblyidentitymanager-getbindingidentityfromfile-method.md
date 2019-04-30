---
title: Método ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3d5e53dd0845fbd01dbd9d20ce8feef12748c04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985173"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="ea419-102">Método ICLRAssemblyIdentityManager::GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="ea419-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="ea419-103">Obtém a identidade do assembly a associação de dados para o assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ea419-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea419-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea419-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea419-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea419-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="ea419-106">[in] O caminho para o arquivo a ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="ea419-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ea419-107">[in] Um valor igual a [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeração que indica o tipo de identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="ea419-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="ea419-108">Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="ea419-108">Provided for future extensibility.</span></span> <span data-ttu-id="ea419-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que o common language runtime (CLR) versão 2.0 dá suporte.</span><span class="sxs-lookup"><span data-stu-id="ea419-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="ea419-110">[out] Um buffer que contém os dados de identidade do assembly opaco.</span><span class="sxs-lookup"><span data-stu-id="ea419-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="ea419-111">[no, out] Um ponteiro para o tamanho de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ea419-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea419-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ea419-112">Return Value</span></span>  
  
|<span data-ttu-id="ea419-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea419-113">HRESULT</span></span>|<span data-ttu-id="ea419-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea419-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea419-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea419-115">S_OK</span></span>|<span data-ttu-id="ea419-116">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ea419-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="ea419-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ea419-117">E_INVALIDARG</span></span>|<span data-ttu-id="ea419-118">Fornecido `pwzFilePath` é nulo.</span><span class="sxs-lookup"><span data-stu-id="ea419-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="ea419-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ea419-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ea419-120">O tamanho de `pwzBuffer` é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="ea419-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="ea419-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea419-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea419-122">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ea419-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea419-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea419-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea419-124">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="ea419-124">The call timed out.</span></span>|  
|<span data-ttu-id="ea419-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea419-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea419-126">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ea419-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea419-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea419-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea419-128">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="ea419-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea419-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea419-129">E_FAIL</span></span>|<span data-ttu-id="ea419-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ea419-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea419-131">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ea419-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea419-132">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea419-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea419-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea419-133">Remarks</span></span>  
 <span data-ttu-id="ea419-134">`GetBindingIdentityFromFile` normalmente é chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="ea419-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="ea419-135">A primeira chamada fornece um valor nulo para `pwzBuffer`, e o método retorna o tamanho apropriado no `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="ea419-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="ea419-136">A segunda chamada fornece um buffer alocado adequadamente e o método retorna com os dados reais do buffer após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="ea419-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea419-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea419-137">Requirements</span></span>  
 <span data-ttu-id="ea419-138">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea419-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea419-139">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea419-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea419-140">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ea419-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea419-141">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea419-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea419-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea419-142">See also</span></span>

- [<span data-ttu-id="ea419-143">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="ea419-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ea419-144">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="ea419-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="ea419-145">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ea419-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
