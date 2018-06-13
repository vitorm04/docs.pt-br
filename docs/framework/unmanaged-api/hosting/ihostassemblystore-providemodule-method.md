---
title: Método IHostAssemblyStore::ProvideModule
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b604e1d7fc3d3c8adf7d95bd95843bc0110dbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440012"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="4aafd-102">Método IHostAssemblyStore::ProvideModule</span><span class="sxs-lookup"><span data-stu-id="4aafd-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="4aafd-103">Resolve um arquivo de recurso do módulo dentro de um assembly ou vinculado (mas não inserida).</span><span class="sxs-lookup"><span data-stu-id="4aafd-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aafd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4aafd-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4aafd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4aafd-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="4aafd-106">[in] Um ponteiro para um [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) a instância que descreve o módulo solicitado <xref:System.AppDomain>, assembly e o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="4aafd-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="4aafd-107">[out] Um ponteiro para um identificador exclusivo para o `IStream` que contém o módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="4aafd-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="4aafd-108">[out] Um ponteiro para o endereço de um `IStream` do objeto, que contém a imagem de PE (executável portátil) a ser carregado, ou nulo se o módulo não pôde ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="4aafd-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="4aafd-109">[out] Um ponteiro para o endereço de um `IStream` do objeto, que contém as informações de depuração (PDB) do programa para o módulo solicitado, ou nulo se não foi possível encontrar o arquivo. PDB.</span><span class="sxs-lookup"><span data-stu-id="4aafd-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4aafd-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4aafd-110">Return Value</span></span>  
  
|<span data-ttu-id="4aafd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4aafd-111">HRESULT</span></span>|<span data-ttu-id="4aafd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4aafd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4aafd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4aafd-113">S_OK</span></span>|<span data-ttu-id="4aafd-114">`ProvideModule` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="4aafd-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="4aafd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4aafd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4aafd-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4aafd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4aafd-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4aafd-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4aafd-118">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="4aafd-118">The call timed out.</span></span>|  
|<span data-ttu-id="4aafd-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4aafd-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4aafd-120">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4aafd-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4aafd-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4aafd-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4aafd-122">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="4aafd-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4aafd-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4aafd-123">E_FAIL</span></span>|<span data-ttu-id="4aafd-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4aafd-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4aafd-125">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4aafd-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4aafd-126">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4aafd-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4aafd-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="4aafd-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="4aafd-128">O recurso vinculado ou o assembly solicitado não pôde ser localizado.</span><span class="sxs-lookup"><span data-stu-id="4aafd-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="4aafd-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4aafd-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4aafd-130">`pdwModuleId` não é grande o suficiente para conter o identificador de host deseja retornar.</span><span class="sxs-lookup"><span data-stu-id="4aafd-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aafd-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="4aafd-131">Remarks</span></span>  
 <span data-ttu-id="4aafd-132">O valor de identidade é retornado para `pdwModuleId` é especificado pelo host.</span><span class="sxs-lookup"><span data-stu-id="4aafd-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="4aafd-133">Identificadores devem ser exclusivos dentro do tempo de vida de um processo.</span><span class="sxs-lookup"><span data-stu-id="4aafd-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="4aafd-134">O CLR usa esse valor como o identificador exclusivo para o fluxo associado.</span><span class="sxs-lookup"><span data-stu-id="4aafd-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="4aafd-135">Ele verifica que cada valor em relação aos valores de `pAssemblyId` retornado por chamadas para [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) e com os valores para `pdwModuleId` retornado por outras chamadas `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="4aafd-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="4aafd-136">Se o host retorna o mesmo valor de identificador para outro `IStream`, o CLR verifica se o conteúdo de fluxo já foi mapeado.</span><span class="sxs-lookup"><span data-stu-id="4aafd-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="4aafd-137">Nesse caso, o CLR carrega a cópia existente da imagem em vez de mapeamento de um novo.</span><span class="sxs-lookup"><span data-stu-id="4aafd-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="4aafd-138">Portanto, o identificador também não deve sobrepor os identificadores de assembly retornados de `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="4aafd-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aafd-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4aafd-139">Requirements</span></span>  
 <span data-ttu-id="4aafd-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aafd-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aafd-141">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4aafd-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4aafd-142">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4aafd-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4aafd-143">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aafd-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aafd-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4aafd-144">See Also</span></span>  
 [<span data-ttu-id="4aafd-145">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="4aafd-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="4aafd-146">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="4aafd-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="4aafd-147">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="4aafd-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
