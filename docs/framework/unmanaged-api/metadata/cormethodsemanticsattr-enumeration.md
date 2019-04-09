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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e36cb91c3ef741badb04b54e2b62158ecf6ced1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134492"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="72df7-102">Enumeração CorMethodSemanticsAttr</span><span class="sxs-lookup"><span data-stu-id="72df7-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="72df7-103">Contém valores que descrevem a relação entre um método e um evento ou propriedade associada.</span><span class="sxs-lookup"><span data-stu-id="72df7-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72df7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72df7-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="72df7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="72df7-105">Members</span></span>  
  
|<span data-ttu-id="72df7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="72df7-106">Member</span></span>|<span data-ttu-id="72df7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="72df7-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="72df7-108">Especifica que o método é um `set` acessador para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="72df7-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="72df7-109">Especifica que o método é um `get` acessador para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="72df7-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="72df7-110">Especifica que o método tem uma relação com uma propriedade ou um evento diferente daqueles definidos aqui.</span><span class="sxs-lookup"><span data-stu-id="72df7-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="72df7-111">Especifica que o método adiciona métodos do manipulador para um evento.</span><span class="sxs-lookup"><span data-stu-id="72df7-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="72df7-112">Especifica que o método Remove métodos do manipulador para um evento.</span><span class="sxs-lookup"><span data-stu-id="72df7-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="72df7-113">Especifica que o método gera um evento.</span><span class="sxs-lookup"><span data-stu-id="72df7-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72df7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72df7-114">Requirements</span></span>  
 <span data-ttu-id="72df7-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72df7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72df7-116">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="72df7-116">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="72df7-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="72df7-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72df7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72df7-118">See also</span></span>

- [<span data-ttu-id="72df7-119">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="72df7-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
