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
ms.openlocfilehash: 4e75b8553ff33946654a6a3b6184f98049c6a6cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126675"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="b0eb1-102">Método ICLRAssemblyReferenceList::IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="b0eb1-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="b0eb1-103">Obtém um valor que indica se o ponteiro fornecido refere-se a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0eb1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0eb1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0eb1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0eb1-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b0eb1-106">no Um ponteiro de interface para o assembly para o qual Pesquisar.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="b0eb1-107">Os valores válidos são do tipo `IAssemblyName` ou `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0eb1-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b0eb1-108">Return Value</span></span>  
  
|<span data-ttu-id="b0eb1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0eb1-109">HRESULT</span></span>|<span data-ttu-id="b0eb1-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0eb1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0eb1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0eb1-111">S_OK</span></span>|<span data-ttu-id="b0eb1-112">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="b0eb1-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b0eb1-113">S_FALSE</span></span>|<span data-ttu-id="b0eb1-114">A cadeia de caracteres não aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="b0eb1-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b0eb1-115">E_FAIL</span></span>|<span data-ttu-id="b0eb1-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b0eb1-117">Depois que um método retorna E_FAIL, o Common Language Runtime não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="b0eb1-118">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0eb1-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0eb1-119">Requirements</span></span>  
 <span data-ttu-id="b0eb1-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0eb1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0eb1-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b0eb1-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0eb1-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b0eb1-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0eb1-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0eb1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0eb1-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0eb1-124">See also</span></span>

- [<span data-ttu-id="b0eb1-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b0eb1-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b0eb1-126">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b0eb1-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b0eb1-127">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="b0eb1-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="b0eb1-128">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="b0eb1-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
