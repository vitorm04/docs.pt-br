---
title: "Método IHostAssemblyStore::ProvideAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2097c1ea64e5e9a2a09e0ec57243624b05eeea65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="6ef1b-102">Método IHostAssemblyStore::ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="6ef1b-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="6ef1b-103">Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que é retornado de [Ihostassemblymanager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="6ef1b-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="6ef1b-104">O common language runtime (CLR) chama `ProvideAssembly` para cada assembly que não aparecem na lista.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ef1b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ef1b-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ef1b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ef1b-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="6ef1b-107">[in] Um ponteiro para um [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instância que o host usa para determinar a certas características de ligação, incluindo a presença ou ausência de qualquer política de controle de versão e qual assembly para associar a.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="6ef1b-108">[out] Um ponteiro para um identificador exclusivo para o assembly solicitado para este `IStream`.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="6ef1b-109">[out] Um ponteiro para dados de host específico que são usados para determinar a evidência do assembly solicitado sem a necessidade de uma plataforma de chamada de invocação.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="6ef1b-110">`pHostContext`corresponde do <xref:System.Reflection.Assembly.HostContext%2A> propriedade gerenciada <xref:System.Reflection.Assembly> classe.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="6ef1b-111">[out] Um ponteiro para o endereço de um `IStream` que contém a imagem de PE (executável portátil) a ser carregado, ou nulo se não foi possível encontrar o assembly.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="6ef1b-112">[out] Um ponteiro para o endereço de um `IStream` que contém informações de depuração (PDB) do programa, ou nulo se o arquivo. PDB não pôde ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ef1b-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6ef1b-113">Return Value</span></span>  
  
|<span data-ttu-id="6ef1b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ef1b-114">HRESULT</span></span>|<span data-ttu-id="6ef1b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ef1b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ef1b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ef1b-116">S_OK</span></span>|<span data-ttu-id="6ef1b-117">`ProvideAssembly`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="6ef1b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ef1b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ef1b-119">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ef1b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ef1b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ef1b-121">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-121">The call timed out.</span></span>|  
|<span data-ttu-id="6ef1b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ef1b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ef1b-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ef1b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ef1b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ef1b-125">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ef1b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ef1b-126">E_FAIL</span></span>|<span data-ttu-id="6ef1b-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ef1b-128">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ef1b-129">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6ef1b-130">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="6ef1b-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="6ef1b-131">O assembly solicitado não pôde ser localizado.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="6ef1b-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6ef1b-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6ef1b-133">O tamanho do buffer especificado por `pAssemblyId` não é grande o suficiente para manter o identificador que o host deseja retornar.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ef1b-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ef1b-134">Remarks</span></span>  
 <span data-ttu-id="6ef1b-135">O valor de identidade é retornado para `pAssemblyId` é especificado pelo host.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="6ef1b-136">Identificadores devem ser exclusivos dentro do tempo de vida de um processo.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="6ef1b-137">O CLR usa esse valor como um identificador exclusivo para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="6ef1b-138">Ele verifica que cada valor em relação aos valores de `pAssemblyId` retornado por outras chamadas `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="6ef1b-139">Se o host retorna o mesmo `pAssemblyId` valor para outro `IStream`, o CLR verifica se o conteúdo de fluxo já foi mapeado.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="6ef1b-140">Nesse caso, o tempo de execução carrega a cópia existente da imagem em vez de mapeamento de um novo.</span><span class="sxs-lookup"><span data-stu-id="6ef1b-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ef1b-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ef1b-141">Requirements</span></span>  
 <span data-ttu-id="6ef1b-142">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ef1b-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ef1b-143">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ef1b-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ef1b-144">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6ef1b-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ef1b-145">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ef1b-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef1b-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ef1b-146">See Also</span></span>  
 [<span data-ttu-id="6ef1b-147">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="6ef1b-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="6ef1b-148">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="6ef1b-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="6ef1b-149">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="6ef1b-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
