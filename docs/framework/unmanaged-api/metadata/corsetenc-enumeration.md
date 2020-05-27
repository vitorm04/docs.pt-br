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
ms.openlocfilehash: 93a194ea72ab894544927cf96304397b7211b5ac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009152"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="a07d6-102">Enumeração CorSetENC</span><span class="sxs-lookup"><span data-stu-id="a07d6-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="a07d6-103">Contém valores usados para influenciar o comportamento durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="a07d6-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a07d6-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a07d6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a07d6-105">Members</span></span>  
  
|<span data-ttu-id="a07d6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a07d6-106">Member</span></span>|<span data-ttu-id="a07d6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a07d6-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="a07d6-108">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a07d6-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="a07d6-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a07d6-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="a07d6-110">Indica que, enquanto os metadados podem ser atualizados, os tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="a07d6-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="a07d6-111">Indica que os tokens podem ser movidos durante as atualizações.</span><span class="sxs-lookup"><span data-stu-id="a07d6-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="a07d6-112">Indica que as atualizações podem consistir apenas em adições.</span><span class="sxs-lookup"><span data-stu-id="a07d6-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="a07d6-113">Tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="a07d6-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="a07d6-114">Indica que a compilação é incremental.</span><span class="sxs-lookup"><span data-stu-id="a07d6-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="a07d6-115">Indica que somente os metadados alterados devem ser salvos.</span><span class="sxs-lookup"><span data-stu-id="a07d6-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="a07d6-116">Inclui `MDUpdateENC` o `MDUpdateFull` e o `MDUpdateIncremental` .</span><span class="sxs-lookup"><span data-stu-id="a07d6-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a07d6-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a07d6-117">Requirements</span></span>  
 <span data-ttu-id="a07d6-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a07d6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a07d6-119">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a07d6-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a07d6-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a07d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07d6-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="a07d6-121">See also</span></span>

- [<span data-ttu-id="a07d6-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="a07d6-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
