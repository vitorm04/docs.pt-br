---
title: Enumeração CorPropertyAttr
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: b6651f30e0df3a5ffc29d310b9067e76761dcf01
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007527"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="fb563-102">Enumeração CorPropertyAttr</span><span class="sxs-lookup"><span data-stu-id="fb563-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="fb563-103">Contém valores que descrevem os metadados de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="fb563-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb563-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb563-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="fb563-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fb563-105">Members</span></span>  
  
|<span data-ttu-id="fb563-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fb563-106">Member</span></span>|<span data-ttu-id="fb563-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb563-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="fb563-108">Especifica que a propriedade é especial e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="fb563-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="fb563-109">Reservado para uso interno pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="fb563-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="fb563-110">Especifica que os Common Language Runtime APIs internas de metadados devem verificar a codificação do nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="fb563-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="fb563-111">Especifica que a propriedade tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="fb563-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="fb563-112">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="fb563-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb563-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb563-113">Requirements</span></span>  
 <span data-ttu-id="fb563-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb563-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb563-115">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="fb563-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fb563-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb563-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb563-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb563-117">See also</span></span>

- [<span data-ttu-id="fb563-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="fb563-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
