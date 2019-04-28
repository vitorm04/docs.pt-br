---
title: Enumeração CorManifestResourceFlags
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 204f04b1ed1ea293639e0b9826f7e0ce6f384763
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992687"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="600a5-102">Enumeração CorManifestResourceFlags</span><span class="sxs-lookup"><span data-stu-id="600a5-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="600a5-103">Indica a visibilidade de recursos codificados em um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="600a5-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="600a5-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="600a5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="600a5-105">Members</span></span>  
  
|<span data-ttu-id="600a5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="600a5-106">Member</span></span>|<span data-ttu-id="600a5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="600a5-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="600a5-108">Reservado.</span><span class="sxs-lookup"><span data-stu-id="600a5-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="600a5-109">Os recursos são públicos.</span><span class="sxs-lookup"><span data-stu-id="600a5-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="600a5-110">Os recursos são privados.</span><span class="sxs-lookup"><span data-stu-id="600a5-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="600a5-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="600a5-111">Requirements</span></span>  
 <span data-ttu-id="600a5-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="600a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="600a5-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="600a5-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="600a5-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="600a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600a5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="600a5-115">See also</span></span>

- [<span data-ttu-id="600a5-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="600a5-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
