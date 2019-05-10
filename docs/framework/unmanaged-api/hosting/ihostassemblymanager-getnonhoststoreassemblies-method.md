---
title: Método IHostAssemblyManager::GetNonHostStoreAssemblies
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 750263f5620569ec1d51a4eebe7ea5d74bb84df2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650291"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="6f904-102">Método IHostAssemblyManager::GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="6f904-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="6f904-103">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que representa a lista de assemblies que o host espera que o common language runtime (CLR) para carregar.</span><span class="sxs-lookup"><span data-stu-id="6f904-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f904-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f904-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f904-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f904-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="6f904-106">[out] Um ponteiro para o endereço de um `ICLRAssemblyReferenceList` que contém uma lista de referências a assemblies que o host espera para carregar o CLR.</span><span class="sxs-lookup"><span data-stu-id="6f904-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f904-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6f904-107">Return Value</span></span>  
  
|<span data-ttu-id="6f904-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f904-108">HRESULT</span></span>|<span data-ttu-id="6f904-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f904-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f904-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f904-110">S_OK</span></span>|<span data-ttu-id="6f904-111">`GetNonHostStoreAssemblies` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6f904-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="6f904-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f904-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f904-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6f904-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f904-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f904-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f904-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6f904-115">The call timed out.</span></span>|  
|<span data-ttu-id="6f904-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f904-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f904-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6f904-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f904-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f904-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f904-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="6f904-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f904-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f904-120">E_FAIL</span></span>|<span data-ttu-id="6f904-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6f904-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f904-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="6f904-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f904-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f904-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6f904-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6f904-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6f904-125">Não havia memória suficiente disponível para criar a lista de referências para a operação `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="6f904-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f904-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f904-126">Remarks</span></span>  
 <span data-ttu-id="6f904-127">O CLR resolve referências usando o seguinte conjunto de diretrizes:</span><span class="sxs-lookup"><span data-stu-id="6f904-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="6f904-128">Primeiro, ele consulta a lista de referências de assembly retornado por `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="6f904-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="6f904-129">Se o assembly aparece na lista, o CLR é associado a ele normalmente.</span><span class="sxs-lookup"><span data-stu-id="6f904-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="6f904-130">Se o assembly não aparece na lista e o host tiver fornecido uma implementação de [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), o CLR chama [ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) para permitir que o host fornecer a assembly para associar a.</span><span class="sxs-lookup"><span data-stu-id="6f904-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="6f904-131">Caso contrário, o CLR não vincular ao assembly.</span><span class="sxs-lookup"><span data-stu-id="6f904-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="6f904-132">Se o host define `ppReferenceList` como nulo, as sondas CLR primeiro chama o cache de assembly global, `ProvideAssembly`e, em seguida, investiga a base do aplicativo para resolver uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="6f904-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f904-133">Após a inicialização, o CLR chama `GetNonHostStoreAssemblies` apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="6f904-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="6f904-134">O método não é chamado novamente.</span><span class="sxs-lookup"><span data-stu-id="6f904-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f904-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f904-135">Requirements</span></span>  
 <span data-ttu-id="6f904-136">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f904-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f904-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f904-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f904-138">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6f904-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f904-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f904-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f904-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f904-140">See also</span></span>

- [<span data-ttu-id="6f904-141">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="6f904-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6f904-142">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="6f904-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="6f904-143">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="6f904-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
