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
ms.openlocfilehash: d19ca92db6f57a004dca54f6e22db10603c9498a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214839"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="8d02f-102">Interface IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8d02f-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="8d02f-103">Serve como o enumerador para uma coleção de `IDefinitionIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="8d02f-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d02f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d02f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8d02f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8d02f-105">Methods</span></span>  
  
|<span data-ttu-id="8d02f-106">Método</span><span class="sxs-lookup"><span data-stu-id="8d02f-106">Method</span></span>|<span data-ttu-id="8d02f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d02f-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="8d02f-108">Obtém um ponteiro de interface para um novo `IEnumDefinitionIdentity` objeto que contém os mesmos membros que isso `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8d02f-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="8d02f-109">Obtém o número especificado de `IDefinitionIdentity` objetos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="8d02f-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="8d02f-110">Move o ponteiro de instrução para o início deste `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8d02f-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="8d02f-111">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="8d02f-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d02f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d02f-112">Requirements</span></span>  
 <span data-ttu-id="8d02f-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d02f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d02f-114">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="8d02f-114">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="8d02f-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8d02f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8d02f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d02f-116">See also</span></span>

- [<span data-ttu-id="8d02f-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="8d02f-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="8d02f-118">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8d02f-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
