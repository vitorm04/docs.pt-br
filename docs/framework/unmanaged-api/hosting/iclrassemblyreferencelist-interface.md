---
title: Interface ICLRAssemblyReferenceList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c2b383abdc67546749867de154a00fda244b3ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660015"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="c2fa9-102">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="c2fa9-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="c2fa9-103">Gerencia uma lista de assemblies que são carregados pelo common language runtime (CLR) e não pelo host.</span><span class="sxs-lookup"><span data-stu-id="c2fa9-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2fa9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c2fa9-104">Methods</span></span>  
  
|<span data-ttu-id="c2fa9-105">Método</span><span class="sxs-lookup"><span data-stu-id="c2fa9-105">Method</span></span>|<span data-ttu-id="c2fa9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2fa9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2fa9-107">Método IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="c2fa9-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="c2fa9-108">Obtém um valor que indica se o ponteiro fornecido faz referência a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="c2fa9-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="c2fa9-109">Método IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="c2fa9-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="c2fa9-110">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="c2fa9-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2fa9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2fa9-111">Remarks</span></span>  
 <span data-ttu-id="c2fa9-112">Chame o [iclrassemblyidentitymanager:: Getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) método para obter um ponteiro para uma instância de `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="c2fa9-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2fa9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2fa9-113">Requirements</span></span>  
 <span data-ttu-id="c2fa9-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2fa9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2fa9-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2fa9-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2fa9-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c2fa9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2fa9-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2fa9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2fa9-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2fa9-118">See also</span></span>
- [<span data-ttu-id="c2fa9-119">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="c2fa9-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c2fa9-120">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="c2fa9-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="c2fa9-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="c2fa9-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
