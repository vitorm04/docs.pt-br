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
ms.openlocfilehash: a1a50c15071ea1e696e508c779309225c7e7bfa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097815"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="44db4-102">Enumeração CorEventAttr</span><span class="sxs-lookup"><span data-stu-id="44db4-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="44db4-103">Contém valores que descrevem os metadados de um evento.</span><span class="sxs-lookup"><span data-stu-id="44db4-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44db4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44db4-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="44db4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="44db4-105">Members</span></span>  
  
|<span data-ttu-id="44db4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="44db4-106">Member</span></span>|<span data-ttu-id="44db4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="44db4-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="44db4-108">Especifica que o evento é especial, e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="44db4-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="44db4-109">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="44db4-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="44db4-110">Especifica que o common language runtime deve verificar a codificação do nome do evento.</span><span class="sxs-lookup"><span data-stu-id="44db4-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44db4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44db4-111">Requirements</span></span>  
 <span data-ttu-id="44db4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44db4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44db4-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="44db4-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="44db4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44db4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44db4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44db4-115">See also</span></span>

- [<span data-ttu-id="44db4-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="44db4-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
