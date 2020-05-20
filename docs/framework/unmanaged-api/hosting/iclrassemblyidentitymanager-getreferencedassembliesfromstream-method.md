---
title: Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
ms.openlocfilehash: 4f06dd7b85446eec986055418d2cf558b9b5bd7a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615924"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="19374-102">Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="19374-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="19374-103">Obtém um ponteiro para um objeto [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) que contém dados de identidade de assembly para os assemblies referenciados pelo assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="19374-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19374-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19374-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19374-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19374-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="19374-106">no Um ponteiro de interface para um `IStream` que contém o assembly a ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="19374-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="19374-107">no Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="19374-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="19374-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor para o qual a versão atual do Common Language Runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="19374-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="19374-109">no Um ponteiro para um objeto [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) que contém dados de identidade de assembly para os assemblies a serem excluídos `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="19374-109">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="19374-110">fora Um ponteiro para o endereço de um `ICLRReferenceAssemblyEnum` objeto que contém dados de identidade de assembly para os assemblies referenciados pelo assembly no `pStream` , excluindo os assemblies no `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="19374-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19374-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="19374-111">Return Value</span></span>  
  
|<span data-ttu-id="19374-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19374-112">HRESULT</span></span>|<span data-ttu-id="19374-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="19374-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19374-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="19374-114">S_OK</span></span>|<span data-ttu-id="19374-115">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="19374-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="19374-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19374-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19374-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="19374-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19374-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19374-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19374-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="19374-119">The call timed out.</span></span>|  
|<span data-ttu-id="19374-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19374-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19374-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="19374-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19374-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19374-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19374-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="19374-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19374-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19374-124">E_FAIL</span></span>|<span data-ttu-id="19374-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="19374-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19374-126">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="19374-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19374-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="19374-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19374-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="19374-128">Remarks</span></span>  
 <span data-ttu-id="19374-129">O chamador pode optar por excluir um conjunto de referências de assembly conhecidas da lista retornada.</span><span class="sxs-lookup"><span data-stu-id="19374-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="19374-130">Esse conjunto é definido por `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="19374-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19374-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19374-131">Requirements</span></span>  
 <span data-ttu-id="19374-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19374-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19374-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19374-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19374-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="19374-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19374-135">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19374-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19374-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="19374-136">See also</span></span>

- [<span data-ttu-id="19374-137">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="19374-137">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="19374-138">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="19374-138">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="19374-139">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="19374-139">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
