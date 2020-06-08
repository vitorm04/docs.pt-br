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
ms.openlocfilehash: 68261b165847a5c3ee29adbc4908451fb00c5443
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492259"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="830c2-102">Método IMetaDataImport::EnumFieldsWithName</span><span class="sxs-lookup"><span data-stu-id="830c2-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="830c2-103">Enumera os tokens FieldDef do tipo especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="830c2-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="830c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="830c2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="830c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="830c2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="830c2-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="830c2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="830c2-107">no O token do tipo cujos campos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="830c2-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="830c2-108">no O nome do campo que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="830c2-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="830c2-109">fora Matriz usada para armazenar os tokens FieldDef.</span><span class="sxs-lookup"><span data-stu-id="830c2-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="830c2-110">no O tamanho máximo da `rFields` matriz.</span><span class="sxs-lookup"><span data-stu-id="830c2-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="830c2-111">fora O número real de tokens FieldDef retornados em `rFields` .</span><span class="sxs-lookup"><span data-stu-id="830c2-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="830c2-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="830c2-112">Remarks</span></span>  
 <span data-ttu-id="830c2-113">Ao contrário de [IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` descarta todos os tokens de campo que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="830c2-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="830c2-114">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="830c2-114">Return Value</span></span>  
  
|<span data-ttu-id="830c2-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="830c2-115">HRESULT</span></span>|<span data-ttu-id="830c2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="830c2-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="830c2-117">`EnumFieldsWithName`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="830c2-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="830c2-118">Não há campos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="830c2-118">There are no fields to enumerate.</span></span> <span data-ttu-id="830c2-119">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="830c2-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="830c2-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="830c2-120">Requirements</span></span>  
 <span data-ttu-id="830c2-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="830c2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="830c2-122">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="830c2-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="830c2-123">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="830c2-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="830c2-124">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="830c2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="830c2-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="830c2-125">See also</span></span>

- [<span data-ttu-id="830c2-126">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="830c2-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="830c2-127">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="830c2-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
