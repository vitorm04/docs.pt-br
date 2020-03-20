---
title: Método IMetaDataImport::EnumFieldsWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177350"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="d9385-102">Método IMetaDataImport::EnumFieldsWithName</span><span class="sxs-lookup"><span data-stu-id="d9385-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="d9385-103">Enumera os tokens FieldDef do tipo especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d9385-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9385-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9385-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9385-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9385-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d9385-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="d9385-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="d9385-107">[em] O símbolo do tipo cujos campos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="d9385-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="d9385-108">[em] O nome de campo que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="d9385-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="d9385-109">[fora] Array usado para armazenar os tokens FieldDef.</span><span class="sxs-lookup"><span data-stu-id="d9385-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d9385-110">[em] O tamanho máximo `rFields` da matriz.</span><span class="sxs-lookup"><span data-stu-id="d9385-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d9385-111">[fora] O número real de tokens FieldDef retornou em `rFields`.</span><span class="sxs-lookup"><span data-stu-id="d9385-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9385-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9385-112">Remarks</span></span>  
 <span data-ttu-id="d9385-113">Ao contrário [do IMetaDataImport::EnumFields,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md) `EnumFieldsWithName` descarta todos os tokens de campo que não tenham o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d9385-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9385-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d9385-114">Return Value</span></span>  
  
|<span data-ttu-id="d9385-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9385-115">HRESULT</span></span>|<span data-ttu-id="d9385-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9385-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d9385-117">`EnumFieldsWithName`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d9385-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d9385-118">Não há campos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="d9385-118">There are no fields to enumerate.</span></span> <span data-ttu-id="d9385-119">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="d9385-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9385-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9385-120">Requirements</span></span>  
 <span data-ttu-id="d9385-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9385-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9385-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9385-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9385-123">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9385-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9385-124">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9385-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9385-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9385-125">See also</span></span>

- [<span data-ttu-id="d9385-126">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d9385-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d9385-127">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d9385-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
