---
title: Enumeração CorSetENC
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432765"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="3d2c4-102">Enumeração CorSetENC</span><span class="sxs-lookup"><span data-stu-id="3d2c4-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="3d2c4-103">Contém valores usados para influenciar o comportamento durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d2c4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="3d2c4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3d2c4-105">Members</span></span>  
  
|<span data-ttu-id="3d2c4-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3d2c4-106">Member</span></span>|<span data-ttu-id="3d2c4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d2c4-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="3d2c4-108">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="3d2c4-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="3d2c4-110">Indica que, enquanto os metadados podem ser atualizados, os tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="3d2c4-111">Indica que os tokens podem ser movidos durante as atualizações.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="3d2c4-112">Indica que as atualizações podem consistir apenas em adições.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="3d2c4-113">Tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="3d2c4-114">Indica que a compilação é incremental.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="3d2c4-115">Indica que somente os metadados alterados devem ser salvos.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="3d2c4-116">Inclui `MDUpdateENC`, `MDUpdateFull` e `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="3d2c4-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d2c4-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3d2c4-117">Requirements</span></span>  
 <span data-ttu-id="3d2c4-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d2c4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d2c4-119">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3d2c4-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3d2c4-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d2c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d2c4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d2c4-121">See also</span></span>

- [<span data-ttu-id="3d2c4-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="3d2c4-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
