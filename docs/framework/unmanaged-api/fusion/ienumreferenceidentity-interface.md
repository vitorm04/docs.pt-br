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
ms.openlocfilehash: 766b17bae0c58d9872ff9c118f330ebc3220257e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697245"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="eded1-102">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="eded1-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="eded1-103">Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="eded1-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eded1-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="eded1-104">Methods</span></span>  
  
|<span data-ttu-id="eded1-105">Método</span><span class="sxs-lookup"><span data-stu-id="eded1-105">Method</span></span>|<span data-ttu-id="eded1-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="eded1-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="eded1-107">Obtém um ponteiro de interface para um novo `IEnumReferenceIdentity` que contém os mesmos membros que isso `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="eded1-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="eded1-108">Obtém o número especificado de `IReferenceIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="eded1-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="eded1-109">Move o ponteiro de instrução para o início deste `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="eded1-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="eded1-110">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="eded1-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eded1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eded1-111">Requirements</span></span>  
 <span data-ttu-id="eded1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eded1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eded1-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="eded1-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="eded1-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eded1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eded1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eded1-115">See also</span></span>

- [<span data-ttu-id="eded1-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="eded1-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="eded1-117">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="eded1-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
