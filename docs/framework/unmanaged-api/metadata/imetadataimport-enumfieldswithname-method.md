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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58c6e6685cc5c268d9313457469369d9df25e13b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564140"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="a0d91-102">Método IMetaDataImport::EnumFieldsWithName</span><span class="sxs-lookup"><span data-stu-id="a0d91-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="a0d91-103">Enumera FieldDef tokens do tipo especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="a0d91-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0d91-104">Syntax</span></span>  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0d91-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0d91-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a0d91-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="a0d91-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="a0d91-107">[in] O token do tipo cujos campos são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="a0d91-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="a0d91-108">[in] O nome do campo que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="a0d91-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="a0d91-109">[out] Matriz usada para armazenar os tokens de FieldDef.</span><span class="sxs-lookup"><span data-stu-id="a0d91-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a0d91-110">[in] O tamanho máximo da `rFields` matriz.</span><span class="sxs-lookup"><span data-stu-id="a0d91-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a0d91-111">[out] O número real de tokens FieldDef retornado no `rFields`.</span><span class="sxs-lookup"><span data-stu-id="a0d91-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0d91-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0d91-112">Remarks</span></span>  
 <span data-ttu-id="a0d91-113">Diferentemente [imetadataimport:: Enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` descarta todos os tokens de campo que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="a0d91-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0d91-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a0d91-114">Return Value</span></span>  
  
|<span data-ttu-id="a0d91-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0d91-115">HRESULT</span></span>|<span data-ttu-id="a0d91-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0d91-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a0d91-117">`EnumFieldsWithName` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a0d91-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a0d91-118">Não há nenhum campo para enumerar.</span><span class="sxs-lookup"><span data-stu-id="a0d91-118">There are no fields to enumerate.</span></span> <span data-ttu-id="a0d91-119">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="a0d91-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0d91-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0d91-120">Requirements</span></span>  
 <span data-ttu-id="a0d91-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0d91-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d91-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0d91-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0d91-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a0d91-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0d91-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d91-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d91-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0d91-125">See also</span></span>
- [<span data-ttu-id="a0d91-126">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a0d91-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a0d91-127">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a0d91-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
