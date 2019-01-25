---
title: Método ICLRAssemblyReferenceList::IsAssemblyReferenceInList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d52f38412366880389e963b5ec6af63dcf5d768f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555044"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="376cb-102">Método ICLRAssemblyReferenceList::IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="376cb-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="376cb-103">Obtém um valor que indica se o ponteiro fornecido se refere a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="376cb-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="376cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="376cb-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="376cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="376cb-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="376cb-106">[in] Um ponteiro de interface para o assembly a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="376cb-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="376cb-107">Os valores válidos são do tipo `IAssemblyName` ou `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="376cb-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="376cb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="376cb-108">Return Value</span></span>  
  
|<span data-ttu-id="376cb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="376cb-109">HRESULT</span></span>|<span data-ttu-id="376cb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="376cb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="376cb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="376cb-111">S_OK</span></span>|<span data-ttu-id="376cb-112">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="376cb-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="376cb-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="376cb-113">S_FALSE</span></span>|<span data-ttu-id="376cb-114">A cadeia de caracteres não aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="376cb-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="376cb-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="376cb-115">E_FAIL</span></span>|<span data-ttu-id="376cb-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="376cb-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="376cb-117">Depois que um método retorna E_FAIL, o common language runtime não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="376cb-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="376cb-118">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="376cb-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="376cb-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="376cb-119">Requirements</span></span>  
 <span data-ttu-id="376cb-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="376cb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="376cb-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="376cb-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="376cb-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="376cb-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="376cb-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="376cb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="376cb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="376cb-124">See also</span></span>
- [<span data-ttu-id="376cb-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="376cb-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="376cb-126">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="376cb-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="376cb-127">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="376cb-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="376cb-128">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="376cb-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
