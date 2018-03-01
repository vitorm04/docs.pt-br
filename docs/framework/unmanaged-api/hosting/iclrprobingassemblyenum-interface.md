---
title: Interface ICLRProbingAssemblyEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31f3bfcb2b70bda952f0e4bb43dd8b0067e6ef1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="ca7f4-102">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="ca7f4-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="ca7f4-103">Fornece métodos que permitem que o host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que é internas para o common language runtime (CLR), sem a necessidade de criar ou entender que a identidade.</span><span class="sxs-lookup"><span data-stu-id="ca7f4-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca7f4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ca7f4-104">Methods</span></span>  
  
|<span data-ttu-id="ca7f4-105">Método</span><span class="sxs-lookup"><span data-stu-id="ca7f4-105">Method</span></span>|<span data-ttu-id="ca7f4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca7f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca7f4-107">Método Get</span><span class="sxs-lookup"><span data-stu-id="ca7f4-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="ca7f4-108">Obtém a identidade do assembly no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="ca7f4-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca7f4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca7f4-109">Remarks</span></span>  
 <span data-ttu-id="ca7f4-110">Métodos como [: Getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retornar um `ICLRProbingAssemblyEnum` instância.</span><span class="sxs-lookup"><span data-stu-id="ca7f4-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca7f4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca7f4-111">Requirements</span></span>  
 <span data-ttu-id="ca7f4-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca7f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca7f4-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca7f4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca7f4-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ca7f4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca7f4-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca7f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7f4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca7f4-116">See Also</span></span>  
 [<span data-ttu-id="ca7f4-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="ca7f4-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ca7f4-118">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="ca7f4-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ca7f4-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ca7f4-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
