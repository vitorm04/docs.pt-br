---
title: "Método IHostAssemblyManager::GetNonHostStoreAssemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager.GetNonHostStoreAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35e22e186b290cc4242275976f5109b73e2cf068
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="37825-102">Método IHostAssemblyManager::GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="37825-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="37825-103">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que representa a lista de assemblies que o host espera o common language runtime (CLR) para carregar.</span><span class="sxs-lookup"><span data-stu-id="37825-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37825-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37825-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37825-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37825-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="37825-106">[out] Um ponteiro para o endereço de um `ICLRAssemblyReferenceList` que contém uma lista de referências a assemblies para carregar o CLR espera que o host.</span><span class="sxs-lookup"><span data-stu-id="37825-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37825-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="37825-107">Return Value</span></span>  
  
|<span data-ttu-id="37825-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37825-108">HRESULT</span></span>|<span data-ttu-id="37825-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="37825-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37825-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="37825-110">S_OK</span></span>|<span data-ttu-id="37825-111">`GetNonHostStoreAssemblies`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="37825-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="37825-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37825-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37825-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="37825-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37825-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37825-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37825-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="37825-115">The call timed out.</span></span>|  
|<span data-ttu-id="37825-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37825-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37825-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="37825-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37825-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37825-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37825-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="37825-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37825-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37825-120">E_FAIL</span></span>|<span data-ttu-id="37825-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="37825-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37825-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="37825-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37825-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37825-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="37825-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="37825-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="37825-125">Não havia memória suficiente criar a lista de referências para a solicitação `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="37825-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37825-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="37825-126">Remarks</span></span>  
 <span data-ttu-id="37825-127">O CLR resolve referências usando o seguinte conjunto de diretrizes:</span><span class="sxs-lookup"><span data-stu-id="37825-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="37825-128">Primeiro, a lista de referências de assembly retornado pela consulta `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="37825-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="37825-129">Se o assembly é exibido na lista, o CLR associa a ele normalmente.</span><span class="sxs-lookup"><span data-stu-id="37825-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="37825-130">Se o assembly não aparecem na lista e o host fornece uma implementação de [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), o CLR chama [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) para permitir que o host fornecer o assembly para associar a.</span><span class="sxs-lookup"><span data-stu-id="37825-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="37825-131">Caso contrário, o CLR não vincular ao assembly.</span><span class="sxs-lookup"><span data-stu-id="37825-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="37825-132">Se o host define `ppReferenceList` como nula, os testes do primeiro CLR chama o cache de assembly global, `ProvideAssembly`e, em seguida, testes da base do aplicativo para resolver uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="37825-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37825-133">Na inicialização, o CLR chama `GetNonHostStoreAssemblies` apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="37825-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="37825-134">O método não é chamado novamente.</span><span class="sxs-lookup"><span data-stu-id="37825-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37825-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37825-135">Requirements</span></span>  
 <span data-ttu-id="37825-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37825-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37825-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37825-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37825-138">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="37825-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37825-139">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37825-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37825-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37825-140">See Also</span></span>  
 [<span data-ttu-id="37825-141">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="37825-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="37825-142">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="37825-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="37825-143">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="37825-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
