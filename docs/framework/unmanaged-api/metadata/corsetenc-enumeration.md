---
title: "Enumeração CorSetENC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85a909d92be8bfdb9ada709b54cf252183ff411e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="0f47c-102">Enumeração CorSetENC</span><span class="sxs-lookup"><span data-stu-id="0f47c-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="0f47c-103">Contém valores usados para influenciar o comportamento durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="0f47c-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f47c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f47c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0f47c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0f47c-105">Members</span></span>  
  
|<span data-ttu-id="0f47c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0f47c-106">Member</span></span>|<span data-ttu-id="0f47c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f47c-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="0f47c-108">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="0f47c-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="0f47c-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="0f47c-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="0f47c-110">Indica que, enquanto os metadados podem ser atualizados, tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="0f47c-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="0f47c-111">Indica que os tokens podem ser movidos durante as atualizações.</span><span class="sxs-lookup"><span data-stu-id="0f47c-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="0f47c-112">Indica que as atualizações podem consistir apenas de adições.</span><span class="sxs-lookup"><span data-stu-id="0f47c-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="0f47c-113">Tokens não podem ser movidos.</span><span class="sxs-lookup"><span data-stu-id="0f47c-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="0f47c-114">Indica que a compilação é incremental.</span><span class="sxs-lookup"><span data-stu-id="0f47c-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="0f47c-115">Indica que apenas os metadados alterados devem ser salvo.</span><span class="sxs-lookup"><span data-stu-id="0f47c-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="0f47c-116">Inclui `MDUpdateENC`, `MDUpdateFull` e `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="0f47c-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f47c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f47c-117">Requirements</span></span>  
 <span data-ttu-id="0f47c-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f47c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f47c-119">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="0f47c-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0f47c-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f47c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f47c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f47c-121">See Also</span></span>  
 [<span data-ttu-id="0f47c-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="0f47c-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
