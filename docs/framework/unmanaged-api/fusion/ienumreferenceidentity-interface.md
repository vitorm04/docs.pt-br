---
title: Interface IEnumReferenceIdentity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1af31c72770947c33f358a9689bac6fd95ef53c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="5b099-102">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="5b099-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="5b099-103">Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="5b099-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b099-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5b099-104">Methods</span></span>  
  
|<span data-ttu-id="5b099-105">Método</span><span class="sxs-lookup"><span data-stu-id="5b099-105">Method</span></span>|<span data-ttu-id="5b099-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b099-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="5b099-107">Obtém um ponteiro de interface para um novo `IEnumReferenceIdentity` que contém os mesmos membros este `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5b099-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="5b099-108">Obtém o número especificado de `IReferenceIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5b099-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="5b099-109">Move o ponteiro de instrução para o início deste `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5b099-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="5b099-110">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5b099-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b099-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b099-111">Requirements</span></span>  
 <span data-ttu-id="5b099-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b099-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b099-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="5b099-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="5b099-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b099-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b099-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b099-115">See Also</span></span>  
 [<span data-ttu-id="5b099-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="5b099-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="5b099-117">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="5b099-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
