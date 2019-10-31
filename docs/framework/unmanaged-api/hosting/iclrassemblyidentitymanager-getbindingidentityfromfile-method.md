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
ms.openlocfilehash: 19d6a76d62680be91a7b9721912ca528edde7511
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126751"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="3db2b-102">Método ICLRAssemblyIdentityManager::GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="3db2b-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="3db2b-103">Obtém os dados de associação de identidade do assembly para o assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="3db2b-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3db2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3db2b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3db2b-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="3db2b-106">no O caminho para o arquivo a ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="3db2b-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3db2b-107">no Um valor da enumeração [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) que indica o tipo de identidade de um assembly.</span><span class="sxs-lookup"><span data-stu-id="3db2b-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="3db2b-108">Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="3db2b-108">Provided for future extensibility.</span></span> <span data-ttu-id="3db2b-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor ao qual o Common Language Runtime (CLR) versão 2,0 dá suporte.</span><span class="sxs-lookup"><span data-stu-id="3db2b-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="3db2b-110">fora Um buffer que contém os dados de identidade do assembly opaco.</span><span class="sxs-lookup"><span data-stu-id="3db2b-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="3db2b-111">[entrada, saída] Um ponteiro para o tamanho de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="3db2b-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3db2b-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3db2b-112">Return Value</span></span>  
  
|<span data-ttu-id="3db2b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3db2b-113">HRESULT</span></span>|<span data-ttu-id="3db2b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3db2b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3db2b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3db2b-115">S_OK</span></span>|<span data-ttu-id="3db2b-116">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="3db2b-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="3db2b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3db2b-117">E_INVALIDARG</span></span>|<span data-ttu-id="3db2b-118">O `pwzFilePath` fornecido é nulo.</span><span class="sxs-lookup"><span data-stu-id="3db2b-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="3db2b-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3db2b-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3db2b-120">O tamanho de `pwzBuffer` é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="3db2b-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="3db2b-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3db2b-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3db2b-122">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3db2b-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3db2b-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3db2b-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3db2b-124">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3db2b-124">The call timed out.</span></span>|  
|<span data-ttu-id="3db2b-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3db2b-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3db2b-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3db2b-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3db2b-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3db2b-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3db2b-128">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="3db2b-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3db2b-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3db2b-129">E_FAIL</span></span>|<span data-ttu-id="3db2b-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3db2b-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3db2b-131">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="3db2b-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3db2b-132">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3db2b-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3db2b-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="3db2b-133">Remarks</span></span>  
 <span data-ttu-id="3db2b-134">`GetBindingIdentityFromFile` normalmente é chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="3db2b-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="3db2b-135">A primeira chamada fornece um valor nulo para `pwzBuffer`e o método retorna o tamanho apropriado em `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="3db2b-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="3db2b-136">A segunda chamada fornece um buffer adequadamente alocado e o método retorna com os dados reais do buffer após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="3db2b-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db2b-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3db2b-137">Requirements</span></span>  
 <span data-ttu-id="3db2b-138">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db2b-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db2b-139">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3db2b-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3db2b-140">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3db2b-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3db2b-141">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db2b-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db2b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3db2b-142">See also</span></span>

- [<span data-ttu-id="3db2b-143">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="3db2b-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3db2b-144">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="3db2b-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3db2b-145">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="3db2b-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
