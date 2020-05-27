---
title: Enumeração CorMethodSemanticsAttr
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 1572c206f4a5a5fe0fd189ca84d0bcda2249c6d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007644"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="18aa0-102">Enumeração CorMethodSemanticsAttr</span><span class="sxs-lookup"><span data-stu-id="18aa0-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="18aa0-103">Contém valores que descrevem a relação entre um método e uma propriedade ou evento associado.</span><span class="sxs-lookup"><span data-stu-id="18aa0-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18aa0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18aa0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="18aa0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="18aa0-105">Members</span></span>  
  
|<span data-ttu-id="18aa0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="18aa0-106">Member</span></span>|<span data-ttu-id="18aa0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="18aa0-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="18aa0-108">Especifica que o método é um `set` acessador para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="18aa0-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="18aa0-109">Especifica que o método é um `get` acessador para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="18aa0-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="18aa0-110">Especifica que o método tem uma relação com uma propriedade ou um evento diferente daqueles definidos aqui.</span><span class="sxs-lookup"><span data-stu-id="18aa0-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="18aa0-111">Especifica que o método adiciona métodos de manipulador para um evento.</span><span class="sxs-lookup"><span data-stu-id="18aa0-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="18aa0-112">Especifica que o método Remove métodos de manipulador para um evento.</span><span class="sxs-lookup"><span data-stu-id="18aa0-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="18aa0-113">Especifica que o método gera um evento.</span><span class="sxs-lookup"><span data-stu-id="18aa0-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18aa0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18aa0-114">Requirements</span></span>  
 <span data-ttu-id="18aa0-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18aa0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18aa0-116">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="18aa0-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="18aa0-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18aa0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18aa0-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="18aa0-118">See also</span></span>

- [<span data-ttu-id="18aa0-119">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="18aa0-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
