---
title: "Método ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5456d725f5bb1c11308b72fdb72f6f60d57ea6b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="b36bc-102">Método ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b36bc-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="b36bc-103">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instância na lista fornecida de identidades de assembly parcial.</span><span class="sxs-lookup"><span data-stu-id="b36bc-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b36bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b36bc-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b36bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b36bc-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="b36bc-106">[in] Uma matriz de cadeias de caracteres terminada em nulo no formato "nome de propriedade = valor..." que especificar uma lista de identidades de assembly parcial.</span><span class="sxs-lookup"><span data-stu-id="b36bc-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="b36bc-107">[in] O número de itens em `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="b36bc-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="b36bc-108">[out] Um ponteiro de interface para um `ICLRAssemblyReferenceList` objeto que contém os dados de identidade de assembly para a lista de assemblies especificados em `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="b36bc-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b36bc-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b36bc-109">Return Value</span></span>  
  
|<span data-ttu-id="b36bc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b36bc-110">HRESULT</span></span>|<span data-ttu-id="b36bc-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b36bc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b36bc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b36bc-112">S_OK</span></span>|<span data-ttu-id="b36bc-113">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b36bc-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="b36bc-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b36bc-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b36bc-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b36bc-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b36bc-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b36bc-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b36bc-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b36bc-117">The call timed out.</span></span>|  
|<span data-ttu-id="b36bc-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b36bc-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b36bc-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b36bc-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b36bc-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b36bc-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b36bc-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b36bc-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b36bc-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b36bc-122">E_FAIL</span></span>|<span data-ttu-id="b36bc-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b36bc-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b36bc-124">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b36bc-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b36bc-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b36bc-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b36bc-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b36bc-126">Requirements</span></span>  
 <span data-ttu-id="b36bc-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b36bc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b36bc-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b36bc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b36bc-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b36bc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b36bc-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b36bc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36bc-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b36bc-131">See Also</span></span>  
 [<span data-ttu-id="b36bc-132">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b36bc-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b36bc-133">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b36bc-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
