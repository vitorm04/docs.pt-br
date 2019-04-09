---
title: Estrutura COR_FIELD_OFFSET
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 820c99de1bdb108a24203a3438b1709ca54490b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078116"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="e92be-102">Estrutura COR_FIELD_OFFSET</span><span class="sxs-lookup"><span data-stu-id="e92be-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="e92be-103">Armazena o deslocamento, em uma classe, do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="e92be-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e92be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e92be-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="e92be-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e92be-105">Members</span></span>  
  
|<span data-ttu-id="e92be-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e92be-106">Member</span></span>|<span data-ttu-id="e92be-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e92be-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="e92be-108">Um `mdFieldDef` token de metadados que representa o campo.</span><span class="sxs-lookup"><span data-stu-id="e92be-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="e92be-109">O campo de deslocamento dentro de sua classe.</span><span class="sxs-lookup"><span data-stu-id="e92be-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e92be-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e92be-110">Remarks</span></span>  
 <span data-ttu-id="e92be-111">[Imetadataimport:: Getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) e [imetadataemit:: Setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) métodos usam um parâmetro de tipo `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="e92be-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e92be-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e92be-112">Requirements</span></span>  
 <span data-ttu-id="e92be-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e92be-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e92be-114">**Cabeçalho:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e92be-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 **<span data-ttu-id="e92be-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e92be-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e92be-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e92be-116">See also</span></span>

- [<span data-ttu-id="e92be-117">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="e92be-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="e92be-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e92be-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e92be-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e92be-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
