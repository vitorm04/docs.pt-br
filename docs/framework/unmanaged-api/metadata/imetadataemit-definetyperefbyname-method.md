---
title: Método IMetaDataEmit::DefineTypeRefByName
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93c55cec3d35fd4208a4a8a7c9b235dd10fb9ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156163"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="ef577-102">Método IMetaDataEmit::DefineTypeRefByName</span><span class="sxs-lookup"><span data-stu-id="ef577-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="ef577-103">Obtém os metadados de um token para um tipo que é definido no escopo especificado, que está fora do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="ef577-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef577-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef577-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef577-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef577-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="ef577-106">[in] O token especificando o escopo de resolução.</span><span class="sxs-lookup"><span data-stu-id="ef577-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="ef577-107">Os seguintes tipos de token são válidos:</span><span class="sxs-lookup"><span data-stu-id="ef577-107">The following token types are valid:</span></span>  
  
-   `mdModuleRef`<span data-ttu-id="ef577-108">, se o tipo é definido no mesmo assembly no qual o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="ef577-108">, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   `mdAssemblyRef`<span data-ttu-id="ef577-109">, se o tipo é definido em um assembly diferente no qual o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="ef577-109">, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   `mdTypeRef`<span data-ttu-id="ef577-110">, se o tipo for um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="ef577-110">, if the type is a nested type.</span></span>  
  
-   `mdModule`<span data-ttu-id="ef577-111">, se o tipo é definido no mesmo módulo no qual o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="ef577-111">, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="ef577-112">Nulo, se o tipo é definido globalmente.</span><span class="sxs-lookup"><span data-stu-id="ef577-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="ef577-113">[in] O nome do tipo de destino em Unicode.</span><span class="sxs-lookup"><span data-stu-id="ef577-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="ef577-114">[out] Um ponteiro para o `mdTypeRef` token que é atribuído ao tipo.</span><span class="sxs-lookup"><span data-stu-id="ef577-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef577-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef577-115">Requirements</span></span>  
 <span data-ttu-id="ef577-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef577-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef577-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ef577-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef577-118">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ef577-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ef577-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ef577-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef577-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef577-120">See also</span></span>

- [<span data-ttu-id="ef577-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ef577-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ef577-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ef577-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
