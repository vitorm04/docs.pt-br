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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 313dbd11f1d033f0e15de651b9c130cc98c217e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192804"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="384e2-102">Método IMetaDataImport::EnumFields</span><span class="sxs-lookup"><span data-stu-id="384e2-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="384e2-103">Enumera FieldDef tokens para o tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="384e2-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="384e2-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="384e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="384e2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="384e2-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="384e2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="384e2-107">[in] O token de TypeDef da classe cujos campos são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="384e2-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="384e2-108">[out] A lista de tokens de FieldDef.</span><span class="sxs-lookup"><span data-stu-id="384e2-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="384e2-109">[in] O tamanho máximo da `rFields` matriz.</span><span class="sxs-lookup"><span data-stu-id="384e2-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="384e2-110">[out] O número real de tokens FieldDef retornado no `rFields`.</span><span class="sxs-lookup"><span data-stu-id="384e2-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="384e2-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="384e2-111">Return Value</span></span>  
  
|<span data-ttu-id="384e2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="384e2-112">HRESULT</span></span>|<span data-ttu-id="384e2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="384e2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="384e2-114">`EnumFields` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="384e2-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="384e2-115">Não há nenhum campo para enumerar.</span><span class="sxs-lookup"><span data-stu-id="384e2-115">There are no fields to enumerate.</span></span> <span data-ttu-id="384e2-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="384e2-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="384e2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="384e2-117">Requirements</span></span>  
 <span data-ttu-id="384e2-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="384e2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="384e2-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="384e2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="384e2-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="384e2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="384e2-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="384e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384e2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="384e2-122">See also</span></span>

- [<span data-ttu-id="384e2-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="384e2-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="384e2-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="384e2-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
