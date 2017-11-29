---
title: "Método IMetaDataImport::EnumMethodImpls"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2634642c49c9d95765b6a93048a04ce512b28099
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="fe99d-102">Método IMetaDataImport::EnumMethodImpls</span><span class="sxs-lookup"><span data-stu-id="fe99d-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="fe99d-103">Enumera os tokens de MethodBody e MethodDeclaration que representa os métodos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="fe99d-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe99d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe99d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fe99d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe99d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fe99d-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="fe99d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="fe99d-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="fe99d-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="fe99d-108">[in] Um TypeDef de token para o tipo cujas implementações de método para enumerar.</span><span class="sxs-lookup"><span data-stu-id="fe99d-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="fe99d-109">[out] A matriz para armazenar os tokens de MethodBody.</span><span class="sxs-lookup"><span data-stu-id="fe99d-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="fe99d-110">[out] A matriz para armazenar os tokens de MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="fe99d-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fe99d-111">[in] O tamanho máximo de `rMethodBody` e `rMethodDecl` matrizes.</span><span class="sxs-lookup"><span data-stu-id="fe99d-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="fe99d-112">[in] O número real de métodos retornados em `rMethodBody` e `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="fe99d-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe99d-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fe99d-113">Return Value</span></span>  
  
|<span data-ttu-id="fe99d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe99d-114">HRESULT</span></span>|<span data-ttu-id="fe99d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe99d-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fe99d-116">`EnumMethodImpls`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="fe99d-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fe99d-117">Não há nenhum token de método para enumerar.</span><span class="sxs-lookup"><span data-stu-id="fe99d-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="fe99d-118">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="fe99d-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe99d-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe99d-119">Requirements</span></span>  
 <span data-ttu-id="fe99d-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe99d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe99d-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe99d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe99d-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fe99d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe99d-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe99d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe99d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe99d-124">See Also</span></span>  
 [<span data-ttu-id="fe99d-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fe99d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fe99d-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fe99d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
