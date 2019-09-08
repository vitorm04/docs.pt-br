---
title: Interface IEnumDefinitionIdentity
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88c2513229b6a4183cadbdc78e505910e01e152c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796478"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="b99e8-102">Interface IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="b99e8-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="b99e8-103">Serve como o enumerador para uma coleção `IDefinitionIdentity` de objetos.</span><span class="sxs-lookup"><span data-stu-id="b99e8-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b99e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b99e8-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="b99e8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b99e8-105">Methods</span></span>  
  
|<span data-ttu-id="b99e8-106">Método</span><span class="sxs-lookup"><span data-stu-id="b99e8-106">Method</span></span>|<span data-ttu-id="b99e8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b99e8-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="b99e8-108">Obtém um ponteiro de interface para um `IEnumDefinitionIdentity` novo objeto que contém os mesmos membros que `IEnumDefinitionIdentity`isso.</span><span class="sxs-lookup"><span data-stu-id="b99e8-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="b99e8-109">Obtém o número especificado de `IDefinitionIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="b99e8-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="b99e8-110">Move o ponteiro de instrução para o início dele `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="b99e8-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="b99e8-111">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="b99e8-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b99e8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b99e8-112">Requirements</span></span>  
 <span data-ttu-id="b99e8-113">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b99e8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b99e8-114">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="b99e8-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b99e8-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b99e8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99e8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b99e8-116">See also</span></span>

- [<span data-ttu-id="b99e8-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="b99e8-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b99e8-118">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="b99e8-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
