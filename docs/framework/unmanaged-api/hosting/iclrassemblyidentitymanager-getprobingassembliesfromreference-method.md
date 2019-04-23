---
title: Método ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e926fb2753367370e9aca726806eb8747e32048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153732"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="b7bb7-102">Método ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="b7bb7-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="b7bb7-103">Obtém uma [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerador para as identidades de assembly referenciados pelo assembly com o tipo de identidade especificado.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7bb7-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7bb7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7bb7-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="b7bb7-106">[in] Um valor válido que especifica a arquitetura do processador, conforme definido em Winnt. H.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b7bb7-107">[in] Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="b7bb7-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que a versão atual do common language runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="b7bb7-109">[in] Uma identidade de associação de assembly opaca, normalmente retornada por uma chamada para o [iclrassemblyidentitymanager:: Getbindingidentityfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) ou [iclrassemblyidentitymanager:: Getbindingidentityfromstream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="b7bb7-110">[out] Um ponteiro de interface para um `ICLRProbingAssemblyEnum` enumerador que contém referências aos assemblies referenciados pelo assembly identificado pelo `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7bb7-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b7bb7-111">Return Value</span></span>  
  
|<span data-ttu-id="b7bb7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7bb7-112">HRESULT</span></span>|<span data-ttu-id="b7bb7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7bb7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7bb7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7bb7-114">S_OK</span></span>|<span data-ttu-id="b7bb7-115">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="b7bb7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7bb7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7bb7-117">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7bb7-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7bb7-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7bb7-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-119">The call timed out.</span></span>|  
|<span data-ttu-id="b7bb7-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7bb7-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7bb7-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7bb7-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7bb7-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7bb7-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7bb7-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7bb7-124">E_FAIL</span></span>|<span data-ttu-id="b7bb7-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7bb7-126">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7bb7-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b7bb7-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7bb7-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7bb7-128">Requirements</span></span>  
 <span data-ttu-id="b7bb7-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7bb7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7bb7-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7bb7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7bb7-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b7bb7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7bb7-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7bb7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bb7-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7bb7-133">See also</span></span>

- [<span data-ttu-id="b7bb7-134">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b7bb7-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b7bb7-135">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b7bb7-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b7bb7-136">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="b7bb7-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
