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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2796be32154275387da891683cc5053095f534af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772317"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="faa58-102">Enumeração CorSetENC</span><span class="sxs-lookup"><span data-stu-id="faa58-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="faa58-103">Contém valores usados para influenciar o comportamento durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="faa58-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa58-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faa58-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="faa58-105">Membros</span><span class="sxs-lookup"><span data-stu-id="faa58-105">Members</span></span>  
  
|<span data-ttu-id="faa58-106">Membro</span><span class="sxs-lookup"><span data-stu-id="faa58-106">Member</span></span>|<span data-ttu-id="faa58-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="faa58-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="faa58-108">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="faa58-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="faa58-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="faa58-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="faa58-110">Indica que, ao passo que os metadados podem ser atualizados, tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="faa58-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="faa58-111">Indica que os tokens podem ser movidos durante as atualizações.</span><span class="sxs-lookup"><span data-stu-id="faa58-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="faa58-112">Indica que as atualizações podem consistir apenas adições.</span><span class="sxs-lookup"><span data-stu-id="faa58-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="faa58-113">Tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="faa58-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="faa58-114">Indica que a compilação é incremental.</span><span class="sxs-lookup"><span data-stu-id="faa58-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="faa58-115">Indica que somente metadados alterados devem ser salvos.</span><span class="sxs-lookup"><span data-stu-id="faa58-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="faa58-116">Inclui `MDUpdateENC`, `MDUpdateFull` e `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="faa58-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faa58-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="faa58-117">Requirements</span></span>  
 <span data-ttu-id="faa58-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa58-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa58-119">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="faa58-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="faa58-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa58-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa58-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faa58-121">See also</span></span>

- [<span data-ttu-id="faa58-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="faa58-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
