---
title: "Enumeração CorEventAttr"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorEventAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorEventAttr
helpviewer_keywords: CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a725a40e4c3a447c6cbcacfba311051e781f176
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="1a6f2-102">Enumeração CorEventAttr</span><span class="sxs-lookup"><span data-stu-id="1a6f2-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="1a6f2-103">Contém valores que descrevem os metadados de um evento.</span><span class="sxs-lookup"><span data-stu-id="1a6f2-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a6f2-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="1a6f2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1a6f2-105">Members</span></span>  
  
|<span data-ttu-id="1a6f2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1a6f2-106">Member</span></span>|<span data-ttu-id="1a6f2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a6f2-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="1a6f2-108">Especifica que o evento é especial, e que descreve seu nome como.</span><span class="sxs-lookup"><span data-stu-id="1a6f2-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="1a6f2-109">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1a6f2-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="1a6f2-110">Especifica que o common language runtime deve verificar a codificação do nome do evento.</span><span class="sxs-lookup"><span data-stu-id="1a6f2-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a6f2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a6f2-111">Requirements</span></span>  
 <span data-ttu-id="1a6f2-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a6f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a6f2-113">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="1a6f2-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1a6f2-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a6f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6f2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a6f2-115">See Also</span></span>  
 [<span data-ttu-id="1a6f2-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="1a6f2-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
