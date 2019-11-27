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
ms.openlocfilehash: 193e8788d5a1b28f43f2fb0d4d935a18542dd923
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427497"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="2c729-102">Método IMetaDataImport::EnumMethodImpls</span><span class="sxs-lookup"><span data-stu-id="2c729-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="2c729-103">Enumera os tokens MethodBody e MethodDeclaration que representam métodos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="2c729-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c729-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c729-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2c729-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c729-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2c729-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="2c729-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2c729-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="2c729-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="2c729-108">no Um token de TypeDef para o tipo cujas implementações de método enumeram.</span><span class="sxs-lookup"><span data-stu-id="2c729-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="2c729-109">fora A matriz para armazenar os tokens MethodBody.</span><span class="sxs-lookup"><span data-stu-id="2c729-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="2c729-110">fora A matriz para armazenar os tokens MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="2c729-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2c729-111">no O tamanho máximo das matrizes `rMethodBody` e `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="2c729-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2c729-112">no O número real de métodos retornados em `rMethodBody` e `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="2c729-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c729-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2c729-113">Return Value</span></span>  
  
|<span data-ttu-id="2c729-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c729-114">HRESULT</span></span>|<span data-ttu-id="2c729-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c729-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2c729-116">`EnumMethodImpls` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2c729-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2c729-117">Não há tokens de método para enumerar.</span><span class="sxs-lookup"><span data-stu-id="2c729-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="2c729-118">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="2c729-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c729-119">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2c729-119">Requirements</span></span>  
 <span data-ttu-id="2c729-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c729-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c729-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2c729-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c729-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2c729-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c729-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c729-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c729-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c729-124">See also</span></span>

- [<span data-ttu-id="2c729-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2c729-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2c729-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2c729-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
