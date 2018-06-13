---
title: Interface IEnumReferenceIdentity
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ebc9fe36955bac8b93ec95e9a55fc8ac1197d9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429115"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="9ff9c-102">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="9ff9c-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="9ff9c-103">Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="9ff9c-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ff9c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9ff9c-104">Methods</span></span>  
  
|<span data-ttu-id="9ff9c-105">Método</span><span class="sxs-lookup"><span data-stu-id="9ff9c-105">Method</span></span>|<span data-ttu-id="9ff9c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ff9c-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="9ff9c-107">Obtém um ponteiro de interface para um novo `IEnumReferenceIdentity` que contém os mesmos membros este `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9ff9c-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="9ff9c-108">Obtém o número especificado de `IReferenceIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="9ff9c-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="9ff9c-109">Move o ponteiro de instrução para o início deste `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9ff9c-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="9ff9c-110">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="9ff9c-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ff9c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ff9c-111">Requirements</span></span>  
 <span data-ttu-id="9ff9c-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ff9c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff9c-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="9ff9c-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9ff9c-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ff9c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff9c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ff9c-115">See Also</span></span>  
 [<span data-ttu-id="9ff9c-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="9ff9c-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="9ff9c-117">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="9ff9c-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
