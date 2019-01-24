---
title: Enumeração CorNativeLinkFlags
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf0fdb1e46bfbd17505e255d539547a00eb4764c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694549"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="5079d-102">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="5079d-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="5079d-103">Fornece valores de sinalizador usados pelo vinculador ao vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="5079d-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5079d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5079d-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5079d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5079d-105">Members</span></span>  
  
|<span data-ttu-id="5079d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5079d-106">Member</span></span>|<span data-ttu-id="5079d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5079d-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="5079d-108">Não indica que nenhum sinalizador.</span><span class="sxs-lookup"><span data-stu-id="5079d-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="5079d-109">Indica um `setLastError` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5079d-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="5079d-110">Indica um `nomangle` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5079d-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="5079d-111">Não usado.</span><span class="sxs-lookup"><span data-stu-id="5079d-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5079d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5079d-112">Requirements</span></span>  
 <span data-ttu-id="5079d-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5079d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5079d-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5079d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5079d-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5079d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5079d-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5079d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5079d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5079d-117">See also</span></span>
- [<span data-ttu-id="5079d-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="5079d-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
