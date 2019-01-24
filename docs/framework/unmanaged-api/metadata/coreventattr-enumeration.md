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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34aa954126cc26519aaea963f99299e5557d2c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743044"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="9d80f-102">Enumeração CorEventAttr</span><span class="sxs-lookup"><span data-stu-id="9d80f-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="9d80f-103">Contém valores que descrevem os metadados de um evento.</span><span class="sxs-lookup"><span data-stu-id="9d80f-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d80f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d80f-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="9d80f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9d80f-105">Members</span></span>  
  
|<span data-ttu-id="9d80f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9d80f-106">Member</span></span>|<span data-ttu-id="9d80f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d80f-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="9d80f-108">Especifica que o evento é especial, e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="9d80f-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="9d80f-109">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9d80f-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="9d80f-110">Especifica que o common language runtime deve verificar a codificação do nome do evento.</span><span class="sxs-lookup"><span data-stu-id="9d80f-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d80f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d80f-111">Requirements</span></span>  
 <span data-ttu-id="9d80f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d80f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d80f-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9d80f-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9d80f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d80f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d80f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d80f-115">See also</span></span>
- [<span data-ttu-id="9d80f-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="9d80f-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
