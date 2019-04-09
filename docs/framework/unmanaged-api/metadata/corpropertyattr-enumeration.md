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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1a0fff266e964b506b2dc7c4030caa54abaa5ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171815"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="83008-102">Enumeração CorPropertyAttr</span><span class="sxs-lookup"><span data-stu-id="83008-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="83008-103">Contém valores que descrevem os metadados de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="83008-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83008-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83008-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="83008-105">Membros</span><span class="sxs-lookup"><span data-stu-id="83008-105">Members</span></span>  
  
|<span data-ttu-id="83008-106">Membro</span><span class="sxs-lookup"><span data-stu-id="83008-106">Member</span></span>|<span data-ttu-id="83008-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="83008-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="83008-108">Especifica que a propriedade é especial, e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="83008-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="83008-109">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="83008-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="83008-110">Especifica que os metadados do common language runtime APIs internas deve verificar a codificação do nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="83008-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="83008-111">Especifica que a propriedade tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="83008-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="83008-112">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="83008-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83008-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83008-113">Requirements</span></span>  
 <span data-ttu-id="83008-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83008-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83008-115">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="83008-115">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="83008-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="83008-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83008-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83008-117">See also</span></span>

- [<span data-ttu-id="83008-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="83008-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
