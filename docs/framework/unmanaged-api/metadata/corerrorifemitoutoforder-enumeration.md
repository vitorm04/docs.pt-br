---
title: Enumeração CorErrorIfEmitOutOfOrder
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628ca1b555d80319312450d784981cfed1bda947
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160440"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="3eff2-102">Enumeração CorErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="3eff2-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="3eff2-103">Contém valores de sinalizador para indicam as condições sob as quais uma mensagem de erro deve ser gerada quando metadados é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3eff2-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eff2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3eff2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3eff2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3eff2-105">Members</span></span>  
  
|<span data-ttu-id="3eff2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3eff2-106">Member</span></span>|<span data-ttu-id="3eff2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3eff2-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="3eff2-108">Indica o comportamento padrão, que não geram mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="3eff2-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="3eff2-109">Indica que o compilador não deve gerar mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="3eff2-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="3eff2-110">Indica que o compilador deve gerar uma mensagem de erro quando um campo, a propriedade, o evento, o método ou parâmetro é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3eff2-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="3eff2-111">Indica que o compilador deve gerar uma mensagem de erro quando um método é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3eff2-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="3eff2-112">Indica que o compilador deve gerar uma mensagem de erro quando um campo é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3eff2-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="3eff2-113">Indica que o compilador deve gerar uma mensagem de erro quando um parâmetro é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3eff2-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="3eff2-114">Indica que o compilador deve gerar uma mensagem de erro quando uma propriedade é emitida fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3eff2-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="3eff2-115">Indica que o compilador deve gerar uma mensagem de erro quando um evento é emitido fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3eff2-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eff2-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3eff2-116">Requirements</span></span>  
 <span data-ttu-id="3eff2-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eff2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eff2-118">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3eff2-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3eff2-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eff2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eff2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3eff2-120">See also</span></span>

- [<span data-ttu-id="3eff2-121">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="3eff2-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
