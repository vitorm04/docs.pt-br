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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123481"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="5d220-102">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="5d220-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="5d220-103">Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="5d220-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d220-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5d220-104">Methods</span></span>  
  
|<span data-ttu-id="5d220-105">Método</span><span class="sxs-lookup"><span data-stu-id="5d220-105">Method</span></span>|<span data-ttu-id="5d220-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d220-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="5d220-107">Obtém um ponteiro de interface para um novo `IEnumReferenceIdentity` que contém os mesmos membros que isso `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5d220-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="5d220-108">Obtém o número especificado de `IReferenceIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5d220-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="5d220-109">Move o ponteiro de instrução para o início deste `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5d220-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="5d220-110">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5d220-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d220-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d220-111">Requirements</span></span>  
 <span data-ttu-id="5d220-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d220-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d220-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="5d220-113">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="5d220-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5d220-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d220-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d220-115">See also</span></span>

- [<span data-ttu-id="5d220-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="5d220-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="5d220-117">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="5d220-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
