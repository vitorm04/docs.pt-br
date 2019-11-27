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
ms.openlocfilehash: ec2972605c40f4ba292f5a5f58d6d3efed53f966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443563"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="72860-102">Enumeração CorEventAttr</span><span class="sxs-lookup"><span data-stu-id="72860-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="72860-103">Contém valores que descrevem os metadados de um evento.</span><span class="sxs-lookup"><span data-stu-id="72860-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72860-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72860-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="72860-105">Membros</span><span class="sxs-lookup"><span data-stu-id="72860-105">Members</span></span>  
  
|<span data-ttu-id="72860-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="72860-106">Member</span></span>|<span data-ttu-id="72860-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="72860-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="72860-108">Especifica que o evento é especial e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="72860-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="72860-109">Reservado para uso interno pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="72860-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="72860-110">Especifica que a Common Language Runtime deve verificar a codificação do nome do evento.</span><span class="sxs-lookup"><span data-stu-id="72860-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72860-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="72860-111">Requirements</span></span>  
 <span data-ttu-id="72860-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72860-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72860-113">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="72860-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="72860-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72860-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72860-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72860-115">See also</span></span>

- [<span data-ttu-id="72860-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="72860-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
