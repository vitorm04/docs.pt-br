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
ms.openlocfilehash: fdfbb22d231d16be7757ff5df26a5a010928af54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767053"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="90100-102">Estrutura COR_FIELD_OFFSET</span><span class="sxs-lookup"><span data-stu-id="90100-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="90100-103">Armazena o deslocamento, em uma classe, do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="90100-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90100-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90100-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="90100-105">Membros</span><span class="sxs-lookup"><span data-stu-id="90100-105">Members</span></span>  
  
|<span data-ttu-id="90100-106">Membro</span><span class="sxs-lookup"><span data-stu-id="90100-106">Member</span></span>|<span data-ttu-id="90100-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="90100-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="90100-108">Um `mdFieldDef` token de metadados que representa o campo.</span><span class="sxs-lookup"><span data-stu-id="90100-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="90100-109">O campo de deslocamento dentro de sua classe.</span><span class="sxs-lookup"><span data-stu-id="90100-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90100-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="90100-110">Remarks</span></span>  
 <span data-ttu-id="90100-111">[Imetadataimport:: Getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) e [imetadataemit:: Setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) métodos usam um parâmetro de tipo `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="90100-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90100-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90100-112">Requirements</span></span>  
 <span data-ttu-id="90100-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90100-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90100-114">**Cabeçalho:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="90100-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="90100-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90100-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90100-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90100-116">See also</span></span>

- [<span data-ttu-id="90100-117">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="90100-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="90100-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="90100-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="90100-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="90100-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
