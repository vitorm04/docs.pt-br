---
title: Interface ICLRAssemblyReferenceList
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList
helpviewer_keywords: ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4249616ca46fe5ef09dce4a3e245794a103298c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="b308e-102">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b308e-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="b308e-103">Gerencia uma lista de assemblies que são carregados pelo common language runtime (CLR) e não pelo host.</span><span class="sxs-lookup"><span data-stu-id="b308e-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b308e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b308e-104">Methods</span></span>  
  
|<span data-ttu-id="b308e-105">Método</span><span class="sxs-lookup"><span data-stu-id="b308e-105">Method</span></span>|<span data-ttu-id="b308e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b308e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b308e-107">Método IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="b308e-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="b308e-108">Obtém um valor que indica se o ponteiro fornecido faz referência a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="b308e-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="b308e-109">Método IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="b308e-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="b308e-110">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="b308e-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b308e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b308e-111">Remarks</span></span>  
 <span data-ttu-id="b308e-112">Chamar o [: Getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) método para obter um ponteiro para uma instância de `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="b308e-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b308e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b308e-113">Requirements</span></span>  
 <span data-ttu-id="b308e-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b308e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b308e-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b308e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b308e-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b308e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b308e-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b308e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b308e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b308e-118">See Also</span></span>  
 [<span data-ttu-id="b308e-119">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b308e-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b308e-120">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="b308e-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="b308e-121">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b308e-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
