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
ms.openlocfilehash: 2d32dc8ae59fc1a4a189d849437cc95ea3b94a4d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449543"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="25e2f-102">Método IMetaDataImport::EnumFields</span><span class="sxs-lookup"><span data-stu-id="25e2f-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="25e2f-103">Enumera os tokens FieldDef para o tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="25e2f-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25e2f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25e2f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25e2f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="25e2f-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="25e2f-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="25e2f-107">no O token de TypeDef da classe cujos campos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="25e2f-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="25e2f-108">fora A lista de tokens FieldDef.</span><span class="sxs-lookup"><span data-stu-id="25e2f-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="25e2f-109">no O tamanho máximo da matriz de `rFields`.</span><span class="sxs-lookup"><span data-stu-id="25e2f-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="25e2f-110">fora O número real de tokens FieldDef retornados em `rFields`.</span><span class="sxs-lookup"><span data-stu-id="25e2f-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25e2f-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="25e2f-111">Return Value</span></span>  
  
|<span data-ttu-id="25e2f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25e2f-112">HRESULT</span></span>|<span data-ttu-id="25e2f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="25e2f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="25e2f-114">`EnumFields` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="25e2f-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="25e2f-115">Não há campos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="25e2f-115">There are no fields to enumerate.</span></span> <span data-ttu-id="25e2f-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="25e2f-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25e2f-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="25e2f-117">Requirements</span></span>  
 <span data-ttu-id="25e2f-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25e2f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25e2f-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="25e2f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25e2f-120">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25e2f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25e2f-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25e2f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e2f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25e2f-122">See also</span></span>

- [<span data-ttu-id="25e2f-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="25e2f-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="25e2f-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="25e2f-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
