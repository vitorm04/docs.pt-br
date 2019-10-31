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
ms.openlocfilehash: 09c6431ec885c8b797dc9bb5f5c3ffe21890ccc7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107948"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="a6cbf-102">Interface IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="a6cbf-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="a6cbf-103">Serve como o enumerador para uma coleção de objetos `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a6cbf-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6cbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6cbf-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a6cbf-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a6cbf-105">Methods</span></span>  
  
|<span data-ttu-id="a6cbf-106">Método</span><span class="sxs-lookup"><span data-stu-id="a6cbf-106">Method</span></span>|<span data-ttu-id="a6cbf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6cbf-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="a6cbf-108">Obtém um ponteiro de interface para um novo objeto `IEnumDefinitionIdentity` que contém os mesmos membros que este `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a6cbf-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="a6cbf-109">Obtém o número especificado de objetos de `IDefinitionIdentity`, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="a6cbf-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="a6cbf-110">Move o ponteiro de instrução para o início deste `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a6cbf-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="a6cbf-111">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="a6cbf-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6cbf-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6cbf-112">Requirements</span></span>  
 <span data-ttu-id="a6cbf-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6cbf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6cbf-114">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="a6cbf-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a6cbf-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6cbf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6cbf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6cbf-116">See also</span></span>

- [<span data-ttu-id="a6cbf-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="a6cbf-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="a6cbf-118">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="a6cbf-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
