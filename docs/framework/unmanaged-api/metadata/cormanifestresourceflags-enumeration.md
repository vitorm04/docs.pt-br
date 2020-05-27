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
ms.openlocfilehash: ebdff88e9fdf499b809d56c4c29a906dbef9ec40
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008970"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="2a4de-102">Enumeração CorManifestResourceFlags</span><span class="sxs-lookup"><span data-stu-id="2a4de-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="2a4de-103">Indica a visibilidade dos recursos codificados em um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="2a4de-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a4de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a4de-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2a4de-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2a4de-105">Members</span></span>  
  
|<span data-ttu-id="2a4de-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2a4de-106">Member</span></span>|<span data-ttu-id="2a4de-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a4de-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="2a4de-108">Reservado.</span><span class="sxs-lookup"><span data-stu-id="2a4de-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="2a4de-109">Os recursos são públicos.</span><span class="sxs-lookup"><span data-stu-id="2a4de-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="2a4de-110">Os recursos são privados.</span><span class="sxs-lookup"><span data-stu-id="2a4de-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a4de-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a4de-111">Requirements</span></span>  
 <span data-ttu-id="2a4de-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a4de-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a4de-113">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="2a4de-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2a4de-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a4de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4de-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a4de-115">See also</span></span>

- [<span data-ttu-id="2a4de-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2a4de-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
