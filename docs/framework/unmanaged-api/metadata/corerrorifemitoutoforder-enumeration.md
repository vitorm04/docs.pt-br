---
title: "Enumeração CorErrorIfEmitOutOfOrder"
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
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c049d78d8ba67ec5f08fc2beb584fef4987c9e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="0c277-102">Enumeração CorErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="0c277-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="0c277-103">Contém os valores de sinalizador que indicam as condições sob as quais uma mensagem de erro deve ser gerada quando metadados é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="0c277-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c277-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c277-104">Syntax</span></span>  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="0c277-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0c277-105">Members</span></span>  
  
|<span data-ttu-id="0c277-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0c277-106">Member</span></span>|<span data-ttu-id="0c277-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c277-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="0c277-108">Indica o comportamento padrão, que não geram mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="0c277-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="0c277-109">Indica que o compilador não deve gerar mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="0c277-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="0c277-110">Indica que o compilador deve gerar uma mensagem de erro quando um campo de propriedade, evento, método ou parâmetro é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="0c277-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="0c277-111">Indica que o compilador deve gerar uma mensagem de erro quando um método é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="0c277-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="0c277-112">Indica que o compilador deve gerar uma mensagem de erro quando um campo é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="0c277-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="0c277-113">Indica que o compilador deve gerar uma mensagem de erro quando um parâmetro é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="0c277-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="0c277-114">Indica que o compilador deve gerar uma mensagem de erro quando uma propriedade é emitida fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="0c277-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="0c277-115">Indica que o compilador deve gerar uma mensagem de erro quando um evento é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="0c277-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c277-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c277-116">Requirements</span></span>  
 <span data-ttu-id="0c277-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c277-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c277-118">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="0c277-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0c277-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c277-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c277-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c277-120">See Also</span></span>  
 [<span data-ttu-id="0c277-121">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="0c277-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
