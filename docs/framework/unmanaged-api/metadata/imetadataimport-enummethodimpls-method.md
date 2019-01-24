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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aebfd41a232a3284f79e4229a8845bf5a34f9d1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574762"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="bb5d8-102">Método IMetaDataImport::EnumMethodImpls</span><span class="sxs-lookup"><span data-stu-id="bb5d8-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="bb5d8-103">Enumera MethodBody e MethodDeclaration tokens que representam os métodos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb5d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb5d8-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb5d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb5d8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bb5d8-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bb5d8-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="bb5d8-108">[in] Um TypeDef de token para o tipo cujas implementações de método para enumerar.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="bb5d8-109">[out] A matriz para armazenar os tokens de MethodBody.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="bb5d8-110">[out] A matriz para armazenar os tokens de MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bb5d8-111">[in] O tamanho máximo do `rMethodBody` e `rMethodDecl` matrizes.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bb5d8-112">[in] O número real de métodos retornados na `rMethodBody` e `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb5d8-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bb5d8-113">Return Value</span></span>  
  
|<span data-ttu-id="bb5d8-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb5d8-114">HRESULT</span></span>|<span data-ttu-id="bb5d8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb5d8-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bb5d8-116">`EnumMethodImpls` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bb5d8-117">Não há nenhum token de método para enumerar.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="bb5d8-118">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="bb5d8-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb5d8-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb5d8-119">Requirements</span></span>  
 <span data-ttu-id="bb5d8-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb5d8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb5d8-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb5d8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb5d8-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bb5d8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb5d8-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb5d8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5d8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb5d8-124">See also</span></span>
- [<span data-ttu-id="bb5d8-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="bb5d8-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bb5d8-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="bb5d8-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
