---
title: Método ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
ms.openlocfilehash: 91f174cab4986882df795eb531baedfc0dd43962
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615857"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="7aed2-102">Método ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="7aed2-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="7aed2-103">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="7aed2-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aed2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7aed2-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aed2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7aed2-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="7aed2-106">no O nome do assembly para o qual Pesquisar.</span><span class="sxs-lookup"><span data-stu-id="7aed2-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7aed2-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7aed2-107">Return Value</span></span>  
  
|<span data-ttu-id="7aed2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7aed2-108">HRESULT</span></span>|<span data-ttu-id="7aed2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7aed2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7aed2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7aed2-110">S_OK</span></span>|<span data-ttu-id="7aed2-111">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="7aed2-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="7aed2-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7aed2-112">S_FALSE</span></span>|<span data-ttu-id="7aed2-113">A cadeia de caracteres não aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="7aed2-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="7aed2-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7aed2-114">E_FAIL</span></span>|<span data-ttu-id="7aed2-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7aed2-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7aed2-116">Depois que um método retorna E_FAIL, o Common Language Runtime não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="7aed2-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="7aed2-117">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7aed2-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7aed2-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7aed2-118">Requirements</span></span>  
 <span data-ttu-id="7aed2-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aed2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aed2-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7aed2-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7aed2-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7aed2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7aed2-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aed2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aed2-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="7aed2-123">See also</span></span>

- [<span data-ttu-id="7aed2-124">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="7aed2-124">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="7aed2-125">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="7aed2-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7aed2-126">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="7aed2-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="7aed2-127">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="7aed2-127">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
