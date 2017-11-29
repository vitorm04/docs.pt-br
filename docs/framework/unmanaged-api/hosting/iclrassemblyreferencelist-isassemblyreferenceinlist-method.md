---
title: "Método ICLRAssemblyReferenceList::IsAssemblyReferenceInList"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 923f7f4178d3c310b51ebb7e7df06040ba69f9c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="fc99a-102">Método ICLRAssemblyReferenceList::IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="fc99a-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="fc99a-103">Obtém um valor que indica se o ponteiro fornecido se refere a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="fc99a-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc99a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc99a-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc99a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc99a-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="fc99a-106">[in] Um ponteiro de interface para o assembly que deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="fc99a-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="fc99a-107">Os valores válidos são do tipo `IAssemblyName` ou `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="fc99a-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc99a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fc99a-108">Return Value</span></span>  
  
|<span data-ttu-id="fc99a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc99a-109">HRESULT</span></span>|<span data-ttu-id="fc99a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc99a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc99a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc99a-111">S_OK</span></span>|<span data-ttu-id="fc99a-112">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="fc99a-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="fc99a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fc99a-113">S_FALSE</span></span>|<span data-ttu-id="fc99a-114">A cadeia de caracteres não aparecem na lista.</span><span class="sxs-lookup"><span data-stu-id="fc99a-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="fc99a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc99a-115">E_FAIL</span></span>|<span data-ttu-id="fc99a-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fc99a-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc99a-117">Depois que um método retornará E_FAIL, o common language runtime não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="fc99a-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="fc99a-118">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc99a-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc99a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc99a-119">Requirements</span></span>  
 <span data-ttu-id="fc99a-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc99a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc99a-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc99a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc99a-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fc99a-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc99a-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc99a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc99a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc99a-124">See Also</span></span>  
 [<span data-ttu-id="fc99a-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="fc99a-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="fc99a-126">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="fc99a-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="fc99a-127">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="fc99a-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="fc99a-128">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="fc99a-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
