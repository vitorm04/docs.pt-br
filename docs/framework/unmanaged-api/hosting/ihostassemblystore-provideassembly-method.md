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
ms.openlocfilehash: f97490e89e835716911072dbad5f70d8e55e76e6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805026"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="af956-102">Método IHostAssemblyStore::ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="af956-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="af956-103">Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que é retornado de [IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="af956-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="af956-104">As chamadas de Common Language Runtime (CLR) `ProvideAssembly` para cada assembly que não aparecem na lista.</span><span class="sxs-lookup"><span data-stu-id="af956-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af956-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af956-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af956-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af956-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="af956-107">no Um ponteiro para uma instância [AssemblyBindInfo](assemblybindinfo-structure.md) que o host usa para determinar determinadas características de ligação, incluindo a presença ou a ausência de qualquer política de controle de versão e a qual assembly associar.</span><span class="sxs-lookup"><span data-stu-id="af956-107">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="af956-108">fora Um ponteiro para um identificador exclusivo para o assembly solicitado para isso `IStream` .</span><span class="sxs-lookup"><span data-stu-id="af956-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="af956-109">fora Um ponteiro para dados específicos de host que é usado para determinar a evidência do assembly solicitado sem a necessidade de uma chamada de invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="af956-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="af956-110">`pHostContext`corresponde à <xref:System.Reflection.Assembly.HostContext%2A> propriedade da classe gerenciada <xref:System.Reflection.Assembly> .</span><span class="sxs-lookup"><span data-stu-id="af956-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="af956-111">fora Um ponteiro para o endereço de um `IStream` que contém a imagem executável portátil (PE) a ser carregada, ou NULL se o assembly não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="af956-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="af956-112">fora Um ponteiro para o endereço de um `IStream` que contém as informações de depuração do programa (PDB) ou NULL se não foi possível encontrar o arquivo. pdb.</span><span class="sxs-lookup"><span data-stu-id="af956-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af956-113">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="af956-113">Return Value</span></span>  
  
|<span data-ttu-id="af956-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af956-114">HRESULT</span></span>|<span data-ttu-id="af956-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="af956-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af956-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="af956-116">S_OK</span></span>|<span data-ttu-id="af956-117">`ProvideAssembly`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="af956-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="af956-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af956-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af956-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="af956-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af956-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af956-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af956-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="af956-121">The call timed out.</span></span>|  
|<span data-ttu-id="af956-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af956-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af956-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="af956-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af956-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af956-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af956-125">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="af956-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af956-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af956-126">E_FAIL</span></span>|<span data-ttu-id="af956-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="af956-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af956-128">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="af956-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af956-129">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="af956-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="af956-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="af956-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="af956-131">Não foi possível localizar o assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="af956-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="af956-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="af956-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="af956-133">O tamanho do buffer especificado por `pAssemblyId` não é grande o suficiente para conter o identificador que o host deseja retornar.</span><span class="sxs-lookup"><span data-stu-id="af956-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af956-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="af956-134">Remarks</span></span>  
 <span data-ttu-id="af956-135">O valor de identidade retornado para `pAssemblyId` é especificado pelo host.</span><span class="sxs-lookup"><span data-stu-id="af956-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="af956-136">Os identificadores devem ser exclusivos dentro do tempo de vida de um processo.</span><span class="sxs-lookup"><span data-stu-id="af956-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="af956-137">O CLR usa esse valor como um identificador exclusivo para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="af956-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="af956-138">Ele verifica cada valor em relação aos valores para `pAssemblyId` retornados por outras chamadas para `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="af956-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="af956-139">Se o host retornar o mesmo `pAssemblyId` valor para outro `IStream` , o CLR verificará se o conteúdo desse fluxo já foi mapeado.</span><span class="sxs-lookup"><span data-stu-id="af956-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="af956-140">Nesse caso, o tempo de execução carrega a cópia existente da imagem em vez de mapear uma nova.</span><span class="sxs-lookup"><span data-stu-id="af956-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af956-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af956-141">Requirements</span></span>  
 <span data-ttu-id="af956-142">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af956-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af956-143">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af956-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af956-144">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af956-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af956-145">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af956-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af956-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="af956-146">See also</span></span>

- [<span data-ttu-id="af956-147">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="af956-147">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="af956-148">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="af956-148">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="af956-149">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="af956-149">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
