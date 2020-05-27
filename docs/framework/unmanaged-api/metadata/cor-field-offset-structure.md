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
ms.openlocfilehash: 70fb637cd1edf81be140b0e3306e3b0a483653a6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007982"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="b56c7-102">Estrutura COR_FIELD_OFFSET</span><span class="sxs-lookup"><span data-stu-id="b56c7-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="b56c7-103">Armazena o deslocamento, dentro de uma classe, do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="b56c7-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b56c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b56c7-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="b56c7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b56c7-105">Members</span></span>  
  
|<span data-ttu-id="b56c7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b56c7-106">Member</span></span>|<span data-ttu-id="b56c7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b56c7-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="b56c7-108">Um `mdFieldDef` token de metadados que representa o campo.</span><span class="sxs-lookup"><span data-stu-id="b56c7-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="b56c7-109">O deslocamento do campo dentro de sua classe.</span><span class="sxs-lookup"><span data-stu-id="b56c7-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b56c7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b56c7-110">Remarks</span></span>  
 <span data-ttu-id="b56c7-111">Os métodos [IMetaDataImport:: GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) e [IMetaDataEmit:: SetClassLayout](imetadataemit-setclasslayout-method.md) usam um parâmetro do tipo `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="b56c7-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b56c7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b56c7-112">Requirements</span></span>  
 <span data-ttu-id="b56c7-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b56c7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b56c7-114">**Cabeçalho:** CorHdr. h, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b56c7-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="b56c7-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b56c7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56c7-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b56c7-116">See also</span></span>

- [<span data-ttu-id="b56c7-117">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="b56c7-117">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="b56c7-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b56c7-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b56c7-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b56c7-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
