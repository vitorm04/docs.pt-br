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
ms.openlocfilehash: 98a58c5e686a0650fa62752f6d1d50706d58e8d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698655"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="91200-102">Estrutura COR_FIELD_OFFSET</span><span class="sxs-lookup"><span data-stu-id="91200-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="91200-103">Armazena o deslocamento, em uma classe, do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="91200-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91200-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91200-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="91200-105">Membros</span><span class="sxs-lookup"><span data-stu-id="91200-105">Members</span></span>  
  
|<span data-ttu-id="91200-106">Membro</span><span class="sxs-lookup"><span data-stu-id="91200-106">Member</span></span>|<span data-ttu-id="91200-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="91200-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="91200-108">Um `mdFieldDef` token de metadados que representa o campo.</span><span class="sxs-lookup"><span data-stu-id="91200-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="91200-109">O campo de deslocamento dentro de sua classe.</span><span class="sxs-lookup"><span data-stu-id="91200-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91200-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="91200-110">Remarks</span></span>  
 <span data-ttu-id="91200-111">[Imetadataimport:: Getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) e [imetadataemit:: Setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) métodos usam um parâmetro de tipo `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="91200-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91200-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91200-112">Requirements</span></span>  
 <span data-ttu-id="91200-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91200-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91200-114">**Cabeçalho:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="91200-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="91200-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91200-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91200-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91200-116">See also</span></span>
- [<span data-ttu-id="91200-117">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="91200-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="91200-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="91200-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="91200-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="91200-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
