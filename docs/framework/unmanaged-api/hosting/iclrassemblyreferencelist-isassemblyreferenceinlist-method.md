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
ms.openlocfilehash: 0632a7f5feee87c386d9488a6c989413af68a47f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615885"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="3814d-102">Método ICLRAssemblyReferenceList::IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="3814d-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="3814d-103">Obtém um valor que indica se o ponteiro fornecido refere-se a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="3814d-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3814d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3814d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3814d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3814d-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="3814d-106">no Um ponteiro de interface para o assembly para o qual Pesquisar.</span><span class="sxs-lookup"><span data-stu-id="3814d-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="3814d-107">Os valores válidos são do tipo `IAssemblyName` ou `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="3814d-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3814d-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3814d-108">Return Value</span></span>  
  
|<span data-ttu-id="3814d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3814d-109">HRESULT</span></span>|<span data-ttu-id="3814d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3814d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3814d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3814d-111">S_OK</span></span>|<span data-ttu-id="3814d-112">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="3814d-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="3814d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3814d-113">S_FALSE</span></span>|<span data-ttu-id="3814d-114">A cadeia de caracteres não aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="3814d-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="3814d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3814d-115">E_FAIL</span></span>|<span data-ttu-id="3814d-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3814d-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3814d-117">Depois que um método retorna E_FAIL, o Common Language Runtime não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="3814d-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="3814d-118">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3814d-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3814d-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3814d-119">Requirements</span></span>  
 <span data-ttu-id="3814d-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3814d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3814d-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3814d-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3814d-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3814d-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3814d-123">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3814d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3814d-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="3814d-124">See also</span></span>

- [<span data-ttu-id="3814d-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="3814d-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3814d-126">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="3814d-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3814d-127">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="3814d-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="3814d-128">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="3814d-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
