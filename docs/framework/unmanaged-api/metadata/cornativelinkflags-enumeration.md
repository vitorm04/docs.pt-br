---
title: "Enumeração CorNativeLinkFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c8477ef13c53db6cc4de58c4e707a82e2ab7f650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="90b32-102">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="90b32-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="90b32-103">Fornece valores de sinalizador usados pelo vinculador ao vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="90b32-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90b32-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90b32-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="90b32-105">Membros</span><span class="sxs-lookup"><span data-stu-id="90b32-105">Members</span></span>  
  
|<span data-ttu-id="90b32-106">Membro</span><span class="sxs-lookup"><span data-stu-id="90b32-106">Member</span></span>|<span data-ttu-id="90b32-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="90b32-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="90b32-108">Não indica que nenhum sinalizador.</span><span class="sxs-lookup"><span data-stu-id="90b32-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="90b32-109">Indica um `setLastError` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="90b32-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="90b32-110">Indica um `nomangle` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="90b32-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="90b32-111">Não usado.</span><span class="sxs-lookup"><span data-stu-id="90b32-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90b32-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90b32-112">Requirements</span></span>  
 <span data-ttu-id="90b32-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90b32-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90b32-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90b32-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90b32-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="90b32-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90b32-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90b32-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b32-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90b32-117">See Also</span></span>  
 [<span data-ttu-id="90b32-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="90b32-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
