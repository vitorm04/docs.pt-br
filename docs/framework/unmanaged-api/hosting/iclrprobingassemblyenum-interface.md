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
ms.openlocfilehash: e1e114070f39e75254fc1bc0f8c1bf3e4733d5a2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703376"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="71aea-102">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="71aea-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="71aea-103">Fornece métodos que permitem ao host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que são internas ao Common Language Runtime (CLR), sem a necessidade de criar ou compreender essa identidade.</span><span class="sxs-lookup"><span data-stu-id="71aea-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71aea-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="71aea-104">Methods</span></span>  
  
|<span data-ttu-id="71aea-105">Método</span><span class="sxs-lookup"><span data-stu-id="71aea-105">Method</span></span>|<span data-ttu-id="71aea-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="71aea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71aea-107">Método Get</span><span class="sxs-lookup"><span data-stu-id="71aea-107">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="71aea-108">Obtém a identidade do assembly no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="71aea-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71aea-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="71aea-109">Remarks</span></span>  
 <span data-ttu-id="71aea-110">Métodos como [ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retornam uma `ICLRProbingAssemblyEnum` instância.</span><span class="sxs-lookup"><span data-stu-id="71aea-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71aea-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71aea-111">Requirements</span></span>  
 <span data-ttu-id="71aea-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71aea-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71aea-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="71aea-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71aea-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="71aea-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71aea-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71aea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71aea-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="71aea-116">See also</span></span>

- [<span data-ttu-id="71aea-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="71aea-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="71aea-118">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="71aea-118">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="71aea-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="71aea-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
