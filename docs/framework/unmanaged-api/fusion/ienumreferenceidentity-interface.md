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
ms.openlocfilehash: 1f2ea9d0e20cb67cc36d0b5883e483ce98941b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743212"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="05059-102">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="05059-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="05059-103">Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="05059-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05059-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="05059-104">Methods</span></span>  
  
|<span data-ttu-id="05059-105">Método</span><span class="sxs-lookup"><span data-stu-id="05059-105">Method</span></span>|<span data-ttu-id="05059-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="05059-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="05059-107">Obtém um ponteiro de interface para um novo `IEnumReferenceIdentity` que contém os mesmos membros que isso `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="05059-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="05059-108">Obtém o número especificado de `IReferenceIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="05059-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="05059-109">Move o ponteiro de instrução para o início deste `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="05059-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="05059-110">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="05059-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05059-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05059-111">Requirements</span></span>  
 <span data-ttu-id="05059-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05059-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05059-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="05059-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="05059-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05059-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05059-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05059-115">See also</span></span>
- [<span data-ttu-id="05059-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="05059-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="05059-117">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="05059-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
