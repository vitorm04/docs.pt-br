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
ms.openlocfilehash: 21cce26c94d26f6c079fca644a31bf83cd1a6432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="2fa5c-102">Enumeração CorManifestResourceFlags</span><span class="sxs-lookup"><span data-stu-id="2fa5c-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="2fa5c-103">Indica a visibilidade de recursos codificados em um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="2fa5c-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fa5c-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2fa5c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2fa5c-105">Members</span></span>  
  
|<span data-ttu-id="2fa5c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2fa5c-106">Member</span></span>|<span data-ttu-id="2fa5c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fa5c-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="2fa5c-108">Reservado.</span><span class="sxs-lookup"><span data-stu-id="2fa5c-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="2fa5c-109">Os recursos são públicos.</span><span class="sxs-lookup"><span data-stu-id="2fa5c-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="2fa5c-110">Os recursos são privados.</span><span class="sxs-lookup"><span data-stu-id="2fa5c-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fa5c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fa5c-111">Requirements</span></span>  
 <span data-ttu-id="2fa5c-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa5c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa5c-113">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="2fa5c-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2fa5c-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa5c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa5c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fa5c-115">See Also</span></span>  
 [<span data-ttu-id="2fa5c-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2fa5c-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
