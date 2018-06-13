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
ms.openlocfilehash: 6ed8bbbd9699fe707d638bb8d07064e508b6f2fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447766"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="c7a6c-102">Método IMetaDataImport::EnumFieldsWithName</span><span class="sxs-lookup"><span data-stu-id="c7a6c-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="c7a6c-103">Enumera os tokens de FieldDef do tipo especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a6c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7a6c-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c7a6c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7a6c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c7a6c-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="c7a6c-107">[in] O token do tipo cujos campos são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="c7a6c-108">[in] O nome do campo que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="c7a6c-109">[out] Usado para armazenar os tokens de FieldDef de matriz.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c7a6c-110">[in] O tamanho máximo da `rFields` matriz.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c7a6c-111">[out] O número real de tokens FieldDef retornado em `rFields`.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7a6c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7a6c-112">Remarks</span></span>  
 <span data-ttu-id="c7a6c-113">Ao contrário de [: Enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` descarta todos os tokens de campo que não tem o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7a6c-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c7a6c-114">Return Value</span></span>  
  
|<span data-ttu-id="c7a6c-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7a6c-115">HRESULT</span></span>|<span data-ttu-id="c7a6c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7a6c-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c7a6c-117">`EnumFieldsWithName` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c7a6c-118">Não há nenhum campo para enumerar.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-118">There are no fields to enumerate.</span></span> <span data-ttu-id="c7a6c-119">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="c7a6c-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7a6c-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7a6c-120">Requirements</span></span>  
 <span data-ttu-id="c7a6c-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a6c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a6c-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7a6c-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7a6c-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c7a6c-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7a6c-124">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a6c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a6c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7a6c-125">See Also</span></span>  
 [<span data-ttu-id="c7a6c-126">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c7a6c-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c7a6c-127">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c7a6c-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
