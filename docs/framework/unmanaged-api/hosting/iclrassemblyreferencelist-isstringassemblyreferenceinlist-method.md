---
title: "Método ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff0e51327e0e66c2a282ebf46e6036f81d3d568b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="08c19-102">Método ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="08c19-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="08c19-103">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="08c19-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08c19-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08c19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08c19-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="08c19-106">[in] O nome do assembly que deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="08c19-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08c19-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="08c19-107">Return Value</span></span>  
  
|<span data-ttu-id="08c19-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08c19-108">HRESULT</span></span>|<span data-ttu-id="08c19-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="08c19-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08c19-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="08c19-110">S_OK</span></span>|<span data-ttu-id="08c19-111">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="08c19-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="08c19-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="08c19-112">S_FALSE</span></span>|<span data-ttu-id="08c19-113">A cadeia de caracteres não aparecem na lista.</span><span class="sxs-lookup"><span data-stu-id="08c19-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="08c19-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08c19-114">E_FAIL</span></span>|<span data-ttu-id="08c19-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="08c19-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08c19-116">Depois que um método retornará E_FAIL, o common language runtime não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="08c19-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="08c19-117">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="08c19-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08c19-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08c19-118">Requirements</span></span>  
 <span data-ttu-id="08c19-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08c19-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c19-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08c19-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08c19-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="08c19-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08c19-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08c19-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c19-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08c19-123">See Also</span></span>  
 [<span data-ttu-id="08c19-124">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="08c19-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="08c19-125">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="08c19-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="08c19-126">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="08c19-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="08c19-127">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="08c19-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
