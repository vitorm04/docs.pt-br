---
title: Método IMetaDataImport::EnumFields
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: be2845d1d660d86447cfbb6f2845a8e68b727e66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175506"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="68779-102">Método IMetaDataImport::EnumFields</span><span class="sxs-lookup"><span data-stu-id="68779-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="68779-103">Enumera tokens FieldDef para o tipo referenciado pelo token TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="68779-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68779-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68779-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68779-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="68779-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="68779-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="68779-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="68779-107">[em] O token TypeDef da classe cujos campos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="68779-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="68779-108">[fora] A lista de tokens FieldDef.</span><span class="sxs-lookup"><span data-stu-id="68779-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="68779-109">[em] O tamanho máximo `rFields` da matriz.</span><span class="sxs-lookup"><span data-stu-id="68779-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="68779-110">[fora] O número real de tokens FieldDef retornou em `rFields`.</span><span class="sxs-lookup"><span data-stu-id="68779-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68779-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="68779-111">Return Value</span></span>  
  
|<span data-ttu-id="68779-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68779-112">HRESULT</span></span>|<span data-ttu-id="68779-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="68779-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="68779-114">`EnumFields`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="68779-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="68779-115">Não há campos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="68779-115">There are no fields to enumerate.</span></span> <span data-ttu-id="68779-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="68779-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68779-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68779-117">Requirements</span></span>  
 <span data-ttu-id="68779-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68779-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68779-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="68779-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68779-120">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68779-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68779-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68779-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68779-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="68779-122">See also</span></span>

- [<span data-ttu-id="68779-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="68779-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="68779-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="68779-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
