---
title: Método IMetaDataImport::EnumMethodImpls
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175467"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="e5980-102">Método IMetaDataImport::EnumMethodImpls</span><span class="sxs-lookup"><span data-stu-id="e5980-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="e5980-103">Enumera os tokens MethodBody e MethodDeclaration representando métodos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="e5980-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5980-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5980-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdToken     rMethodBody[],
   [out]     mdToken     rMethodDecl[],
   [in]      ULONG       cMax,
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5980-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5980-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e5980-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="e5980-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e5980-107">Isto deve ser NULO para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="e5980-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="e5980-108">[em] Um token TypeDef para o tipo cujo método implementa para enumerar.</span><span class="sxs-lookup"><span data-stu-id="e5980-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="e5980-109">[fora] A matriz para armazenar os tokens MethodBody.</span><span class="sxs-lookup"><span data-stu-id="e5980-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="e5980-110">[fora] A matriz para armazenar os tokens MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="e5980-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e5980-111">[em] O tamanho máximo `rMethodBody` `rMethodDecl` do e matrizes.</span><span class="sxs-lookup"><span data-stu-id="e5980-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e5980-112">[em] O número real de métodos retornou `rMethodBody` e `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="e5980-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5980-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e5980-113">Return Value</span></span>  
  
|<span data-ttu-id="e5980-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5980-114">HRESULT</span></span>|<span data-ttu-id="e5980-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5980-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e5980-116">`EnumMethodImpls`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="e5980-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e5980-117">Não há tokens de método para enumerar.</span><span class="sxs-lookup"><span data-stu-id="e5980-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="e5980-118">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="e5980-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5980-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5980-119">Requirements</span></span>  
 <span data-ttu-id="e5980-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5980-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5980-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5980-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5980-122">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5980-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5980-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5980-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5980-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="e5980-124">See also</span></span>

- [<span data-ttu-id="e5980-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e5980-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e5980-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e5980-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
