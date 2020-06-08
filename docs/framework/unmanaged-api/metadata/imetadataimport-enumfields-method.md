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
ms.openlocfilehash: 1ff2dd64dc4797bc485550c30f7204644a3adb47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492272"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="6bc30-102">Método IMetaDataImport::EnumFields</span><span class="sxs-lookup"><span data-stu-id="6bc30-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="6bc30-103">Enumera os tokens FieldDef para o tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="6bc30-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc30-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bc30-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bc30-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bc30-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6bc30-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="6bc30-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="6bc30-107">no O token de TypeDef da classe cujos campos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="6bc30-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="6bc30-108">fora A lista de tokens FieldDef.</span><span class="sxs-lookup"><span data-stu-id="6bc30-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6bc30-109">no O tamanho máximo da `rFields` matriz.</span><span class="sxs-lookup"><span data-stu-id="6bc30-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6bc30-110">fora O número real de tokens FieldDef retornados em `rFields` .</span><span class="sxs-lookup"><span data-stu-id="6bc30-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bc30-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6bc30-111">Return Value</span></span>  
  
|<span data-ttu-id="6bc30-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bc30-112">HRESULT</span></span>|<span data-ttu-id="6bc30-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6bc30-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6bc30-114">`EnumFields`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6bc30-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6bc30-115">Não há campos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="6bc30-115">There are no fields to enumerate.</span></span> <span data-ttu-id="6bc30-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="6bc30-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bc30-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bc30-117">Requirements</span></span>  
 <span data-ttu-id="6bc30-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bc30-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bc30-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6bc30-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6bc30-120">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6bc30-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bc30-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bc30-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc30-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="6bc30-122">See also</span></span>

- [<span data-ttu-id="6bc30-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6bc30-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6bc30-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6bc30-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
