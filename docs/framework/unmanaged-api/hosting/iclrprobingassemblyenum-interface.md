---
title: Interface ICLRProbingAssemblyEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum
helpviewer_keywords: ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6d810ab6e62c6df1b00305947de552ecdbe82141
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="202ae-102">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="202ae-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="202ae-103">Fornece métodos que permitem que o host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que é internas para o common language runtime (CLR), sem a necessidade de criar ou entender que a identidade.</span><span class="sxs-lookup"><span data-stu-id="202ae-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="202ae-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="202ae-104">Methods</span></span>  
  
|<span data-ttu-id="202ae-105">Método</span><span class="sxs-lookup"><span data-stu-id="202ae-105">Method</span></span>|<span data-ttu-id="202ae-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="202ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="202ae-107">Método Get</span><span class="sxs-lookup"><span data-stu-id="202ae-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="202ae-108">Obtém a identidade do assembly no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="202ae-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="202ae-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="202ae-109">Remarks</span></span>  
 <span data-ttu-id="202ae-110">Métodos como [: Getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retornar um `ICLRProbingAssemblyEnum` instância.</span><span class="sxs-lookup"><span data-stu-id="202ae-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="202ae-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="202ae-111">Requirements</span></span>  
 <span data-ttu-id="202ae-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="202ae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="202ae-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="202ae-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="202ae-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="202ae-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="202ae-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="202ae-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202ae-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="202ae-116">See Also</span></span>  
 [<span data-ttu-id="202ae-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="202ae-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="202ae-118">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="202ae-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="202ae-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="202ae-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
