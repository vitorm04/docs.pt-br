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
ms.openlocfilehash: 9211af4726617598f3dd8772383cade6368e6c08
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007618"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="381dc-102">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="381dc-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="381dc-103">Fornece valores de sinalizador usados pelo vinculador ao vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="381dc-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="381dc-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="381dc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="381dc-105">Members</span></span>  
  
|<span data-ttu-id="381dc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="381dc-106">Member</span></span>|<span data-ttu-id="381dc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="381dc-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="381dc-108">Indica que não há sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="381dc-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="381dc-109">Indica uma `setLastError` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="381dc-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="381dc-110">Indica uma `nomangle` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="381dc-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="381dc-111">Não usado.</span><span class="sxs-lookup"><span data-stu-id="381dc-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="381dc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="381dc-112">Requirements</span></span>  
 <span data-ttu-id="381dc-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="381dc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="381dc-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="381dc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="381dc-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="381dc-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="381dc-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="381dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381dc-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="381dc-117">See also</span></span>

- [<span data-ttu-id="381dc-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="381dc-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
