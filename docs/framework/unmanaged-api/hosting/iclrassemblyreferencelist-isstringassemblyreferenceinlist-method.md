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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ed527aadce68e82bee5809aab7c4229a95b5d3f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478837"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="91b49-102">Método ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="91b49-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="91b49-103">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="91b49-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91b49-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91b49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91b49-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="91b49-106">[in] O nome do assembly para o qual pesquisar.</span><span class="sxs-lookup"><span data-stu-id="91b49-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91b49-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="91b49-107">Return Value</span></span>  
  
|<span data-ttu-id="91b49-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91b49-108">HRESULT</span></span>|<span data-ttu-id="91b49-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="91b49-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91b49-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="91b49-110">S_OK</span></span>|<span data-ttu-id="91b49-111">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="91b49-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="91b49-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="91b49-112">S_FALSE</span></span>|<span data-ttu-id="91b49-113">A cadeia de caracteres não aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="91b49-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="91b49-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91b49-114">E_FAIL</span></span>|<span data-ttu-id="91b49-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="91b49-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91b49-116">Depois que um método retorna E_FAIL, o common language runtime não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="91b49-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="91b49-117">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="91b49-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91b49-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91b49-118">Requirements</span></span>  
 <span data-ttu-id="91b49-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91b49-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91b49-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="91b49-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91b49-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="91b49-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91b49-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91b49-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b49-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91b49-123">See also</span></span>
- [<span data-ttu-id="91b49-124">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="91b49-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="91b49-125">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="91b49-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="91b49-126">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="91b49-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="91b49-127">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="91b49-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
