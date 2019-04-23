---
title: Interface ICLRProbingAssemblyEnum
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 118345f246de3d7ee68d51cf37e8cdea9de1fdba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094288"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="d0d7d-102">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="d0d7d-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="d0d7d-103">Fornece métodos que permitem que o host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que é internas para o common language runtime (CLR), sem a necessidade de criar ou entender essa identidade.</span><span class="sxs-lookup"><span data-stu-id="d0d7d-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0d7d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d0d7d-104">Methods</span></span>  
  
|<span data-ttu-id="d0d7d-105">Método</span><span class="sxs-lookup"><span data-stu-id="d0d7d-105">Method</span></span>|<span data-ttu-id="d0d7d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0d7d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0d7d-107">Método Get</span><span class="sxs-lookup"><span data-stu-id="d0d7d-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="d0d7d-108">Obtém a identidade do assembly no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="d0d7d-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0d7d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0d7d-109">Remarks</span></span>  
 <span data-ttu-id="d0d7d-110">Métodos como [iclrassemblyidentitymanager:: Getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retornar um `ICLRProbingAssemblyEnum` instância.</span><span class="sxs-lookup"><span data-stu-id="d0d7d-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d7d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0d7d-111">Requirements</span></span>  
 <span data-ttu-id="d0d7d-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d7d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0d7d-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0d7d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0d7d-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d0d7d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0d7d-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d7d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d7d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0d7d-116">See also</span></span>

- [<span data-ttu-id="d0d7d-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="d0d7d-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d0d7d-118">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="d0d7d-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d0d7d-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="d0d7d-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
