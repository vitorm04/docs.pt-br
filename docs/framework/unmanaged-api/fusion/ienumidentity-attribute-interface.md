---
title: Interface IEnumIDENTITY_ATTRIBUTE
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796460"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="c2dc5-102">Interface IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="c2dc5-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="c2dc5-103">Serve como um enumerador para os atributos do objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="c2dc5-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2dc5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c2dc5-104">Methods</span></span>  
  
|<span data-ttu-id="c2dc5-105">Método</span><span class="sxs-lookup"><span data-stu-id="c2dc5-105">Method</span></span>|<span data-ttu-id="c2dc5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2dc5-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="c2dc5-107">Obtém um ponteiro de interface para um `IEnumIDENTITY_ATTRIBUTE` novo que contém os mesmos membros que `IEnumIDENTITY_ATTRIBUTE`isso.</span><span class="sxs-lookup"><span data-stu-id="c2dc5-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="c2dc5-108">Grava os dados contidos nos elementos `IEnumIDENTITY_ATTRIBUTE` deste para o buffer de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="c2dc5-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="c2dc5-109">Obtém o número especificado de atributos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="c2dc5-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="c2dc5-110">Move o ponteiro de instrução para o início dele `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="c2dc5-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="c2dc5-111">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="c2dc5-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2dc5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2dc5-112">Requirements</span></span>  
 <span data-ttu-id="c2dc5-113">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2dc5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2dc5-114">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="c2dc5-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c2dc5-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2dc5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2dc5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2dc5-116">See also</span></span>

- [<span data-ttu-id="c2dc5-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="c2dc5-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
