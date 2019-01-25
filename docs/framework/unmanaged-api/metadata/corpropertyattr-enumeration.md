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
ms.openlocfilehash: 713913fa046fc1bef12b8849ac82e4399a8dc534
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577565"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="d2d08-102">Enumeração CorPropertyAttr</span><span class="sxs-lookup"><span data-stu-id="d2d08-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="d2d08-103">Contém valores que descrevem os metadados de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="d2d08-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2d08-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="d2d08-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d2d08-105">Members</span></span>  
  
|<span data-ttu-id="d2d08-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d2d08-106">Member</span></span>|<span data-ttu-id="d2d08-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2d08-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="d2d08-108">Especifica que a propriedade é especial, e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="d2d08-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="d2d08-109">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d2d08-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="d2d08-110">Especifica que os metadados do common language runtime APIs internas deve verificar a codificação do nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d2d08-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="d2d08-111">Especifica que a propriedade tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="d2d08-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="d2d08-112">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="d2d08-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2d08-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2d08-113">Requirements</span></span>  
 <span data-ttu-id="d2d08-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2d08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2d08-115">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d2d08-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d2d08-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2d08-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d08-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2d08-117">See also</span></span>
- [<span data-ttu-id="d2d08-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="d2d08-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
