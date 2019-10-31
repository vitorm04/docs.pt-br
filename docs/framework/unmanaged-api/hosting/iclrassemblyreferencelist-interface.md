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
ms.openlocfilehash: e74d49d71cfee51f8cb99645151aace3d02de0e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126661"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="b1d1b-102">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b1d1b-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="b1d1b-103">Gerencia uma lista de assemblies que são carregados pelo Common Language Runtime (CLR) e não pelo host.</span><span class="sxs-lookup"><span data-stu-id="b1d1b-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1d1b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b1d1b-104">Methods</span></span>  
  
|<span data-ttu-id="b1d1b-105">Método</span><span class="sxs-lookup"><span data-stu-id="b1d1b-105">Method</span></span>|<span data-ttu-id="b1d1b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1d1b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1d1b-107">Método IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="b1d1b-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="b1d1b-108">Obtém um valor que indica se o ponteiro fornecido faz referência a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="b1d1b-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="b1d1b-109">Método IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="b1d1b-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="b1d1b-110">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="b1d1b-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1d1b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1d1b-111">Remarks</span></span>  
 <span data-ttu-id="b1d1b-112">Chame o método [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) para obter um ponteiro para uma instância de `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="b1d1b-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d1b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1d1b-113">Requirements</span></span>  
 <span data-ttu-id="b1d1b-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d1b-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1d1b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1d1b-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1d1b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1d1b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d1b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d1b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1d1b-118">See also</span></span>

- [<span data-ttu-id="b1d1b-119">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b1d1b-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b1d1b-120">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="b1d1b-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="b1d1b-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b1d1b-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
