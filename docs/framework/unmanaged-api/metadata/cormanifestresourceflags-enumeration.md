---
title: "Enumeração CorManifestResourceFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorManifestResourceFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorManifestResourceFlags
helpviewer_keywords: CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5cdaba8b1186d1720ff8b64f50a8effc4691fe8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="adf78-102">Enumeração CorManifestResourceFlags</span><span class="sxs-lookup"><span data-stu-id="adf78-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="adf78-103">Indica a visibilidade de recursos codificados em um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="adf78-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adf78-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adf78-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="adf78-105">Membros</span><span class="sxs-lookup"><span data-stu-id="adf78-105">Members</span></span>  
  
|<span data-ttu-id="adf78-106">Membro</span><span class="sxs-lookup"><span data-stu-id="adf78-106">Member</span></span>|<span data-ttu-id="adf78-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="adf78-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="adf78-108">Reservado.</span><span class="sxs-lookup"><span data-stu-id="adf78-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="adf78-109">Os recursos são públicos.</span><span class="sxs-lookup"><span data-stu-id="adf78-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="adf78-110">Os recursos são privados.</span><span class="sxs-lookup"><span data-stu-id="adf78-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adf78-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="adf78-111">Requirements</span></span>  
 <span data-ttu-id="adf78-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adf78-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adf78-113">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="adf78-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="adf78-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adf78-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf78-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adf78-115">See Also</span></span>  
 [<span data-ttu-id="adf78-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="adf78-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
