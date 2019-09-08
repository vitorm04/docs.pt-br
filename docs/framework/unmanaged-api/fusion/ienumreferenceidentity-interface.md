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
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796437"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="378bd-102">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="378bd-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="378bd-103">Serve como um enumerador para uma coleção `IReferenceIdentity` de objetos.</span><span class="sxs-lookup"><span data-stu-id="378bd-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="378bd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="378bd-104">Methods</span></span>  
  
|<span data-ttu-id="378bd-105">Método</span><span class="sxs-lookup"><span data-stu-id="378bd-105">Method</span></span>|<span data-ttu-id="378bd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="378bd-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="378bd-107">Obtém um ponteiro de interface para um `IEnumReferenceIdentity` novo que contém os mesmos membros que `IEnumReferenceIdentity`isso.</span><span class="sxs-lookup"><span data-stu-id="378bd-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="378bd-108">Obtém o número especificado de `IReferenceIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="378bd-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="378bd-109">Move o ponteiro de instrução para o início dele `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="378bd-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="378bd-110">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="378bd-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="378bd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="378bd-111">Requirements</span></span>  
 <span data-ttu-id="378bd-112">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="378bd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="378bd-113">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="378bd-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="378bd-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="378bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378bd-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="378bd-115">See also</span></span>

- [<span data-ttu-id="378bd-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="378bd-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="378bd-117">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="378bd-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
