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
ms.openlocfilehash: 28e97289eda5949e6d124426eb58105e2e3ad33e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435036"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="38769-102">Método ICLRAssemblyIdentityManager::GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="38769-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="38769-103">Obtém a identidade de assembly a associação de dados para o assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="38769-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38769-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38769-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38769-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38769-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="38769-106">[in] O caminho para o arquivo a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="38769-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="38769-107">[in] Um valor de [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeração que indica o tipo de identidade de um assembly.</span><span class="sxs-lookup"><span data-stu-id="38769-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="38769-108">Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="38769-108">Provided for future extensibility.</span></span> <span data-ttu-id="38769-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que suporta o common language runtime (CLR) versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="38769-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="38769-110">[out] Um buffer que contém os dados de identidade de assembly opaco.</span><span class="sxs-lookup"><span data-stu-id="38769-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="38769-111">[out no] Um ponteiro para o tamanho de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="38769-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38769-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="38769-112">Return Value</span></span>  
  
|<span data-ttu-id="38769-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38769-113">HRESULT</span></span>|<span data-ttu-id="38769-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="38769-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38769-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="38769-115">S_OK</span></span>|<span data-ttu-id="38769-116">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="38769-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="38769-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="38769-117">E_INVALIDARG</span></span>|<span data-ttu-id="38769-118">Fornecido `pwzFilePath` é nulo.</span><span class="sxs-lookup"><span data-stu-id="38769-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="38769-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="38769-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="38769-120">O tamanho de `pwzBuffer` é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="38769-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="38769-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38769-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38769-122">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="38769-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38769-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38769-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38769-124">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="38769-124">The call timed out.</span></span>|  
|<span data-ttu-id="38769-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38769-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38769-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="38769-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38769-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38769-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38769-128">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="38769-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38769-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38769-129">E_FAIL</span></span>|<span data-ttu-id="38769-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="38769-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38769-131">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="38769-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38769-132">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38769-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38769-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="38769-133">Remarks</span></span>  
 <span data-ttu-id="38769-134">`GetBindingIdentityFromFile` geralmente é chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="38769-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="38769-135">A primeira chamada fornece um valor nulo para `pwzBuffer`, e o método retorna o tamanho apropriado em `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="38769-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="38769-136">A segunda chamada fornece um buffer alocado adequadamente e o método retornará com os dados do buffer real após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="38769-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38769-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38769-137">Requirements</span></span>  
 <span data-ttu-id="38769-138">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38769-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38769-139">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38769-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38769-140">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="38769-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38769-141">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38769-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38769-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38769-142">See Also</span></span>  
 [<span data-ttu-id="38769-143">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="38769-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="38769-144">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="38769-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="38769-145">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="38769-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
