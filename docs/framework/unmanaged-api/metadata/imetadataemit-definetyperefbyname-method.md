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
ms.openlocfilehash: 4fd6102b65137a06009428c1245b80c0d44924a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445485"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="77fda-102">Método IMetaDataEmit::DefineTypeRefByName</span><span class="sxs-lookup"><span data-stu-id="77fda-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="77fda-103">Obtém os metadados de um token para um tipo que é definido no escopo especificado, que está fora do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="77fda-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77fda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77fda-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77fda-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77fda-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="77fda-106">[in] O token especificando o escopo de resolução.</span><span class="sxs-lookup"><span data-stu-id="77fda-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="77fda-107">Os seguintes tipos de token são válidos:</span><span class="sxs-lookup"><span data-stu-id="77fda-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="77fda-108">`mdModuleRef`, se o tipo é definido no mesmo assembly no qual o chamador está definido.</span><span class="sxs-lookup"><span data-stu-id="77fda-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="77fda-109">`mdAssemblyRef`, se o tipo é definido em um assembly diferente no qual o chamador está definido.</span><span class="sxs-lookup"><span data-stu-id="77fda-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="77fda-110">`mdTypeRef`, se o tipo for um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="77fda-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="77fda-111">`mdModule`, se o tipo é definido no mesmo módulo no qual o chamador está definido.</span><span class="sxs-lookup"><span data-stu-id="77fda-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="77fda-112">NULL se o tipo é definido globalmente.</span><span class="sxs-lookup"><span data-stu-id="77fda-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="77fda-113">[in] O nome do tipo de destino em Unicode.</span><span class="sxs-lookup"><span data-stu-id="77fda-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="77fda-114">[out] Um ponteiro para o `mdTypeRef` que é atribuído ao tipo de token.</span><span class="sxs-lookup"><span data-stu-id="77fda-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77fda-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77fda-115">Requirements</span></span>  
 <span data-ttu-id="77fda-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77fda-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77fda-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="77fda-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77fda-118">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="77fda-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77fda-119">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77fda-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fda-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77fda-120">See Also</span></span>  
 [<span data-ttu-id="77fda-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="77fda-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="77fda-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="77fda-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
