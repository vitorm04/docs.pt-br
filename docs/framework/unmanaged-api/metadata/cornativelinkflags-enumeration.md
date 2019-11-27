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
ms.openlocfilehash: 1362efbf518310240ce665badc93810d1c0b9b89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450193"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="2a784-102">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="2a784-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="2a784-103">Fornece valores de sinalizador usados pelo vinculador ao vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="2a784-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a784-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a784-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2a784-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2a784-105">Members</span></span>  
  
|<span data-ttu-id="2a784-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2a784-106">Member</span></span>|<span data-ttu-id="2a784-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a784-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="2a784-108">Indica que não há sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="2a784-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="2a784-109">Indica uma palavra-chave `setLastError`.</span><span class="sxs-lookup"><span data-stu-id="2a784-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="2a784-110">Indica uma palavra-chave `nomangle`.</span><span class="sxs-lookup"><span data-stu-id="2a784-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="2a784-111">Não usado.</span><span class="sxs-lookup"><span data-stu-id="2a784-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a784-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2a784-112">Requirements</span></span>  
 <span data-ttu-id="2a784-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a784-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a784-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2a784-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a784-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2a784-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a784-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a784-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a784-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a784-117">See also</span></span>

- [<span data-ttu-id="2a784-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2a784-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
