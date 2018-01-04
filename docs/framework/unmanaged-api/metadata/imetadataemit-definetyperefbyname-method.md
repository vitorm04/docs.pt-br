---
title: "Método IMetaDataEmit::DefineTypeRefByName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46b9fe83a5beb031d4ac21deb903060e2f788e1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="ba54a-102">Método IMetaDataEmit::DefineTypeRefByName</span><span class="sxs-lookup"><span data-stu-id="ba54a-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="ba54a-103">Obtém os metadados de um token para um tipo que é definido no escopo especificado, que está fora do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="ba54a-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba54a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba54a-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba54a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba54a-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="ba54a-106">[in] O token especificando o escopo de resolução.</span><span class="sxs-lookup"><span data-stu-id="ba54a-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="ba54a-107">Os seguintes tipos de token são válidos:</span><span class="sxs-lookup"><span data-stu-id="ba54a-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="ba54a-108">`mdModuleRef`, se o tipo é definido no mesmo assembly no qual o chamador está definido.</span><span class="sxs-lookup"><span data-stu-id="ba54a-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="ba54a-109">`mdAssemblyRef`, se o tipo é definido em um assembly diferente no qual o chamador está definido.</span><span class="sxs-lookup"><span data-stu-id="ba54a-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="ba54a-110">`mdTypeRef`, se o tipo for um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="ba54a-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="ba54a-111">`mdModule`, se o tipo é definido no mesmo módulo no qual o chamador está definido.</span><span class="sxs-lookup"><span data-stu-id="ba54a-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="ba54a-112">NULL se o tipo é definido globalmente.</span><span class="sxs-lookup"><span data-stu-id="ba54a-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="ba54a-113">[in] O nome do tipo de destino em Unicode.</span><span class="sxs-lookup"><span data-stu-id="ba54a-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="ba54a-114">[out] Um ponteiro para o `mdTypeRef` que é atribuído ao tipo de token.</span><span class="sxs-lookup"><span data-stu-id="ba54a-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba54a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba54a-115">Requirements</span></span>  
 <span data-ttu-id="ba54a-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba54a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba54a-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ba54a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba54a-118">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ba54a-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba54a-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba54a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba54a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba54a-120">See Also</span></span>  
 [<span data-ttu-id="ba54a-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ba54a-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ba54a-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ba54a-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
