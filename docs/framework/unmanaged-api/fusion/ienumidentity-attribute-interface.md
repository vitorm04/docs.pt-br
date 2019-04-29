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
ms.openlocfilehash: d725228f2a7359d415673fdcb90d0cabae1a40be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697326"
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="96cfc-102">Interface IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="96cfc-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="96cfc-103">Serve como um enumerador para os atributos do objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="96cfc-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96cfc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="96cfc-104">Methods</span></span>  
  
|<span data-ttu-id="96cfc-105">Método</span><span class="sxs-lookup"><span data-stu-id="96cfc-105">Method</span></span>|<span data-ttu-id="96cfc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="96cfc-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="96cfc-107">Obtém um ponteiro de interface para um novo `IEnumIDENTITY_ATTRIBUTE` que contém os mesmos membros que isso `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="96cfc-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="96cfc-108">Grava os dados contidos em elementos deste `IEnumIDENTITY_ATTRIBUTE` no buffer de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="96cfc-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="96cfc-109">Obtém o número especificado de atributos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="96cfc-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="96cfc-110">Move o ponteiro de instrução para o início deste `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="96cfc-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="96cfc-111">Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="96cfc-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96cfc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96cfc-112">Requirements</span></span>  
 <span data-ttu-id="96cfc-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96cfc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96cfc-114">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="96cfc-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="96cfc-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96cfc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96cfc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96cfc-116">See also</span></span>

- [<span data-ttu-id="96cfc-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="96cfc-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
