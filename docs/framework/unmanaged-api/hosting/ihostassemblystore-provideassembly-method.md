---
title: Método IHostAssemblyStore::ProvideAssembly
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124481"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="d190e-102">Método IHostAssemblyStore::ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="d190e-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="d190e-103">Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que é retornado de [IHostAssemblyManager:: GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="d190e-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="d190e-104">O Common Language Runtime (CLR) chama `ProvideAssembly` para cada assembly que não aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="d190e-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d190e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d190e-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d190e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d190e-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="d190e-107">no Um ponteiro para uma instância [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) que o host usa para determinar determinadas características de ligação, incluindo a presença ou a ausência de qualquer política de controle de versão e a qual assembly associar.</span><span class="sxs-lookup"><span data-stu-id="d190e-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="d190e-108">fora Um ponteiro para um identificador exclusivo para o assembly solicitado para este `IStream`.</span><span class="sxs-lookup"><span data-stu-id="d190e-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="d190e-109">fora Um ponteiro para dados específicos de host que é usado para determinar a evidência do assembly solicitado sem a necessidade de uma chamada de invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="d190e-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="d190e-110">`pHostContext` corresponde à propriedade <xref:System.Reflection.Assembly.HostContext%2A> da classe <xref:System.Reflection.Assembly> gerenciada.</span><span class="sxs-lookup"><span data-stu-id="d190e-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="d190e-111">fora Um ponteiro para o endereço de um `IStream` que contém a imagem do executável portátil (PE) a ser carregada, ou NULL se o assembly não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="d190e-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="d190e-112">fora Um ponteiro para o endereço de um `IStream` que contém as informações de depuração do programa (PDB) ou NULL se não foi possível encontrar o arquivo. pdb.</span><span class="sxs-lookup"><span data-stu-id="d190e-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d190e-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d190e-113">Return Value</span></span>  
  
|<span data-ttu-id="d190e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d190e-114">HRESULT</span></span>|<span data-ttu-id="d190e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d190e-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d190e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="d190e-116">S_OK</span></span>|<span data-ttu-id="d190e-117">`ProvideAssembly` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d190e-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="d190e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d190e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d190e-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d190e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d190e-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d190e-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d190e-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d190e-121">The call timed out.</span></span>|  
|<span data-ttu-id="d190e-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d190e-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d190e-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d190e-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d190e-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d190e-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d190e-125">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="d190e-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d190e-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d190e-126">E_FAIL</span></span>|<span data-ttu-id="d190e-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d190e-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d190e-128">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="d190e-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d190e-129">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d190e-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d190e-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="d190e-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="d190e-131">Não foi possível localizar o assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="d190e-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="d190e-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d190e-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d190e-133">O tamanho do buffer especificado por `pAssemblyId` não é grande o suficiente para manter o identificador que o host deseja retornar.</span><span class="sxs-lookup"><span data-stu-id="d190e-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d190e-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="d190e-134">Remarks</span></span>  
 <span data-ttu-id="d190e-135">O valor de identidade retornado para `pAssemblyId` é especificado pelo host.</span><span class="sxs-lookup"><span data-stu-id="d190e-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="d190e-136">Os identificadores devem ser exclusivos dentro do tempo de vida de um processo.</span><span class="sxs-lookup"><span data-stu-id="d190e-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="d190e-137">O CLR usa esse valor como um identificador exclusivo para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="d190e-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="d190e-138">Ele verifica cada valor em relação aos valores de `pAssemblyId` retornados por outras chamadas para `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="d190e-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="d190e-139">Se o host retornar o mesmo valor de `pAssemblyId` para outro `IStream`, o CLR verificará se o conteúdo desse fluxo já foi mapeado.</span><span class="sxs-lookup"><span data-stu-id="d190e-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="d190e-140">Nesse caso, o tempo de execução carrega a cópia existente da imagem em vez de mapear uma nova.</span><span class="sxs-lookup"><span data-stu-id="d190e-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d190e-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d190e-141">Requirements</span></span>  
 <span data-ttu-id="d190e-142">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d190e-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d190e-143">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d190e-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d190e-144">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d190e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d190e-145">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d190e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d190e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d190e-146">See also</span></span>

- [<span data-ttu-id="d190e-147">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="d190e-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d190e-148">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="d190e-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d190e-149">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="d190e-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
