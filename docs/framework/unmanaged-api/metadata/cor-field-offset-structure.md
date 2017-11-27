---
title: Estrutura COR_FIELD_OFFSET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD_OFFSET
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_FIELD_OFFSET
helpviewer_keywords: COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8e821a9d4ffa5054f687eff7360bc8d7cefb9f09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="fc3c0-102">Estrutura COR_FIELD_OFFSET</span><span class="sxs-lookup"><span data-stu-id="fc3c0-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="fc3c0-103">Armazena o deslocamento, em uma classe, do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="fc3c0-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3c0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc3c0-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="fc3c0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fc3c0-105">Members</span></span>  
  
|<span data-ttu-id="fc3c0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fc3c0-106">Member</span></span>|<span data-ttu-id="fc3c0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc3c0-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="fc3c0-108">Um `mdFieldDef` token de metadados que representa o campo.</span><span class="sxs-lookup"><span data-stu-id="fc3c0-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="fc3c0-109">O campo de deslocamento dentro de sua classe.</span><span class="sxs-lookup"><span data-stu-id="fc3c0-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc3c0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc3c0-110">Remarks</span></span>  
 <span data-ttu-id="fc3c0-111">[: Getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) e [: Setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) métodos usam um parâmetro do tipo `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="fc3c0-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc3c0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc3c0-112">Requirements</span></span>  
 <span data-ttu-id="fc3c0-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc3c0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc3c0-114">**Cabeçalho:** Corhdr, Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="fc3c0-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="fc3c0-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc3c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3c0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc3c0-116">See Also</span></span>  
 [<span data-ttu-id="fc3c0-117">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="fc3c0-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="fc3c0-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="fc3c0-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="fc3c0-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fc3c0-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
