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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094288"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="7252f-102">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="7252f-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="7252f-103">Fornece métodos que permitem que o host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que é internas para o common language runtime (CLR), sem a necessidade de criar ou entender essa identidade.</span><span class="sxs-lookup"><span data-stu-id="7252f-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7252f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7252f-104">Methods</span></span>  
  
|<span data-ttu-id="7252f-105">Método</span><span class="sxs-lookup"><span data-stu-id="7252f-105">Method</span></span>|<span data-ttu-id="7252f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7252f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7252f-107">Método Get</span><span class="sxs-lookup"><span data-stu-id="7252f-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="7252f-108">Obtém a identidade do assembly no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="7252f-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7252f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7252f-109">Remarks</span></span>  
 <span data-ttu-id="7252f-110">Métodos como [iclrassemblyidentitymanager:: Getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retornar um `ICLRProbingAssemblyEnum` instância.</span><span class="sxs-lookup"><span data-stu-id="7252f-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7252f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7252f-111">Requirements</span></span>  
 <span data-ttu-id="7252f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7252f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7252f-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7252f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7252f-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7252f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7252f-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7252f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7252f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7252f-116">See also</span></span>

- [<span data-ttu-id="7252f-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="7252f-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="7252f-118">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="7252f-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7252f-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7252f-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
