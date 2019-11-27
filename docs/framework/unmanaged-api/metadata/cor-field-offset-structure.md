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
ms.openlocfilehash: 646952d5cd55b74081a0ba6171a6eee6b0138512
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443970"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="f1ede-102">Estrutura COR_FIELD_OFFSET</span><span class="sxs-lookup"><span data-stu-id="f1ede-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="f1ede-103">Armazena o deslocamento, dentro de uma classe, do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="f1ede-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1ede-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1ede-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="f1ede-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f1ede-105">Members</span></span>  
  
|<span data-ttu-id="f1ede-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f1ede-106">Member</span></span>|<span data-ttu-id="f1ede-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1ede-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="f1ede-108">Um `mdFieldDef` token de metadados que representa o campo.</span><span class="sxs-lookup"><span data-stu-id="f1ede-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="f1ede-109">O deslocamento do campo dentro de sua classe.</span><span class="sxs-lookup"><span data-stu-id="f1ede-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1ede-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1ede-110">Remarks</span></span>  
 <span data-ttu-id="f1ede-111">Os métodos [IMetaDataImport:: GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) e [IMetaDataEmit:: SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) usam um parâmetro do tipo `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="f1ede-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1ede-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f1ede-112">Requirements</span></span>  
 <span data-ttu-id="f1ede-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1ede-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1ede-114">**Cabeçalho:** CorHdr. h, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="f1ede-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="f1ede-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1ede-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1ede-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1ede-116">See also</span></span>

- [<span data-ttu-id="f1ede-117">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="f1ede-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f1ede-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f1ede-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f1ede-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f1ede-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
