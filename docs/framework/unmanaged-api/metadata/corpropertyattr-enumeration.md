---
title: "Enumeração CorPropertyAttr"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4470cd46653dd798718e5b3413dbc021a894138b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="c952e-102">Enumeração CorPropertyAttr</span><span class="sxs-lookup"><span data-stu-id="c952e-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="c952e-103">Contém valores que descrevem os metadados de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="c952e-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c952e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c952e-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c952e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c952e-105">Members</span></span>  
  
|<span data-ttu-id="c952e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c952e-106">Member</span></span>|<span data-ttu-id="c952e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c952e-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="c952e-108">Especifica que a propriedade é especial, e que descreve seu nome como.</span><span class="sxs-lookup"><span data-stu-id="c952e-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="c952e-109">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c952e-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="c952e-110">Especifica que os metadados de tempo de execução de linguagem comum APIs interno deve verificar a codificação do nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c952e-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="c952e-111">Especifica que a propriedade tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="c952e-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="c952e-112">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="c952e-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c952e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c952e-113">Requirements</span></span>  
 <span data-ttu-id="c952e-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c952e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c952e-115">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="c952e-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c952e-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c952e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c952e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c952e-117">See Also</span></span>  
 [<span data-ttu-id="c952e-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c952e-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
