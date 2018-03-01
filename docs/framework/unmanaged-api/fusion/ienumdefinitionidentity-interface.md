---
title: Interface IEnumDefinitionIdentity
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
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79e2a35a455407715a05e826d31c5d5ab05a02ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="facb5-102">Interface IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="facb5-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="facb5-103">Serve como o enumerador para uma coleção de `IDefinitionIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="facb5-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facb5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="facb5-104">Syntax</span></span>  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="facb5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="facb5-105">Methods</span></span>  
  
|<span data-ttu-id="facb5-106">Método</span><span class="sxs-lookup"><span data-stu-id="facb5-106">Method</span></span>|<span data-ttu-id="facb5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="facb5-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="facb5-108">Obtém um ponteiro de interface para um novo `IEnumDefinitionIdentity` objeto que contém os mesmos membros este `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="facb5-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="facb5-109">Obtém o número especificado de `IDefinitionIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="facb5-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="facb5-110">Move o ponteiro de instrução para o início deste `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="facb5-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="facb5-111">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="facb5-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="facb5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="facb5-112">Requirements</span></span>  
 <span data-ttu-id="facb5-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="facb5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facb5-114">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="facb5-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="facb5-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facb5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facb5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="facb5-116">See Also</span></span>  
 [<span data-ttu-id="facb5-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="facb5-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="facb5-118">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="facb5-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
