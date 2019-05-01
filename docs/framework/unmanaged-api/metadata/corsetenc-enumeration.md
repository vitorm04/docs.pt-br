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
ms.openlocfilehash: 1fd903cb4a9ce664b7a1c958a3fef0c639d6845d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045312"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="38a2f-102">Enumeração CorSetENC</span><span class="sxs-lookup"><span data-stu-id="38a2f-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="38a2f-103">Contém valores usados para influenciar o comportamento durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="38a2f-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38a2f-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="38a2f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="38a2f-105">Members</span></span>  
  
|<span data-ttu-id="38a2f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="38a2f-106">Member</span></span>|<span data-ttu-id="38a2f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="38a2f-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="38a2f-108">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="38a2f-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="38a2f-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="38a2f-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="38a2f-110">Indica que, ao passo que os metadados podem ser atualizados, tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="38a2f-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="38a2f-111">Indica que os tokens podem ser movidos durante as atualizações.</span><span class="sxs-lookup"><span data-stu-id="38a2f-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="38a2f-112">Indica que as atualizações podem consistir apenas adições.</span><span class="sxs-lookup"><span data-stu-id="38a2f-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="38a2f-113">Tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="38a2f-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="38a2f-114">Indica que a compilação é incremental.</span><span class="sxs-lookup"><span data-stu-id="38a2f-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="38a2f-115">Indica que somente metadados alterados devem ser salvos.</span><span class="sxs-lookup"><span data-stu-id="38a2f-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="38a2f-116">Inclui `MDUpdateENC`, `MDUpdateFull` e `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="38a2f-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38a2f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38a2f-117">Requirements</span></span>  
 <span data-ttu-id="38a2f-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38a2f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a2f-119">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="38a2f-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="38a2f-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a2f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a2f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38a2f-121">See also</span></span>

- [<span data-ttu-id="38a2f-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="38a2f-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
