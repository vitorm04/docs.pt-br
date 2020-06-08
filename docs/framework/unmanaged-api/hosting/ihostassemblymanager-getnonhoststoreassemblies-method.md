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
ms.openlocfilehash: 9a1440be7011130b16d7112ae15026eb74856190
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501581"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="f7643-102">Método IHostAssemblyManager::GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="f7643-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="f7643-103">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) que representa a lista de assemblies que o host espera que o Common Language Runtime (CLR) carregue.</span><span class="sxs-lookup"><span data-stu-id="f7643-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7643-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7643-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7643-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7643-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="f7643-106">fora Um ponteiro para o endereço de um `ICLRAssemblyReferenceList` que contém uma lista de referências a assemblies que o host espera que o CLR carregue.</span><span class="sxs-lookup"><span data-stu-id="f7643-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7643-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="f7643-107">Return Value</span></span>  
  
|<span data-ttu-id="f7643-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7643-108">HRESULT</span></span>|<span data-ttu-id="f7643-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7643-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7643-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7643-110">S_OK</span></span>|<span data-ttu-id="f7643-111">`GetNonHostStoreAssemblies`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f7643-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="f7643-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7643-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7643-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f7643-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7643-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7643-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f7643-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f7643-115">The call timed out.</span></span>|  
|<span data-ttu-id="f7643-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f7643-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f7643-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f7643-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f7643-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f7643-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f7643-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="f7643-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f7643-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7643-120">E_FAIL</span></span>|<span data-ttu-id="f7643-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f7643-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f7643-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="f7643-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7643-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f7643-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f7643-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f7643-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f7643-125">Não havia memória suficiente disponível para criar a lista de referências para o solicitado `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="f7643-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7643-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7643-126">Remarks</span></span>  
 <span data-ttu-id="f7643-127">O CLR resolve referências usando o seguinte conjunto de diretrizes:</span><span class="sxs-lookup"><span data-stu-id="f7643-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="f7643-128">Primeiro, ele consulta a lista de referências de assembly retornada por `GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="f7643-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="f7643-129">Se o assembly aparecer na lista, o CLR será associado a ele normalmente.</span><span class="sxs-lookup"><span data-stu-id="f7643-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="f7643-130">Se o assembly não aparecer na lista e o host tiver fornecido uma implementação de [IHostAssemblyStore](ihostassemblystore-interface.md), o CLR chamará [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) para permitir que o host forneça o assembly ao qual associar.</span><span class="sxs-lookup"><span data-stu-id="f7643-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="f7643-131">Caso contrário, o CLR não se associará ao assembly.</span><span class="sxs-lookup"><span data-stu-id="f7643-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="f7643-132">Se o host definir `ppReferenceList` como nulo, o CLR primeiro investigará o cache de assembly global, chamará `ProvideAssembly` e, em seguida, investigará a base do aplicativo para resolver uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="f7643-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7643-133">Na inicialização, o CLR chama `GetNonHostStoreAssemblies` apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f7643-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="f7643-134">O método não é chamado novamente.</span><span class="sxs-lookup"><span data-stu-id="f7643-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7643-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7643-135">Requirements</span></span>  
 <span data-ttu-id="f7643-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7643-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7643-137">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f7643-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7643-138">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f7643-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7643-139">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7643-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7643-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="f7643-140">See also</span></span>

- [<span data-ttu-id="f7643-141">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="f7643-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f7643-142">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="f7643-142">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="f7643-143">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="f7643-143">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
