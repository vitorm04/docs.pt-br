---
title: Enumeração CorEventAttr
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: e22b390271a7813dd1d34aecf5f8a62d7eb81005
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007425"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="c0984-102">Enumeração CorEventAttr</span><span class="sxs-lookup"><span data-stu-id="c0984-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="c0984-103">Contém valores que descrevem os metadados de um evento.</span><span class="sxs-lookup"><span data-stu-id="c0984-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0984-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0984-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c0984-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c0984-105">Members</span></span>  
  
|<span data-ttu-id="c0984-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c0984-106">Member</span></span>|<span data-ttu-id="c0984-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0984-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="c0984-108">Especifica que o evento é especial e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="c0984-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="c0984-109">Reservado para uso interno pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="c0984-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="c0984-110">Especifica que a Common Language Runtime deve verificar a codificação do nome do evento.</span><span class="sxs-lookup"><span data-stu-id="c0984-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0984-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0984-111">Requirements</span></span>  
 <span data-ttu-id="c0984-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0984-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0984-113">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c0984-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c0984-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0984-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0984-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0984-115">See also</span></span>

- [<span data-ttu-id="c0984-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c0984-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
