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
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434387"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="4aba1-102">Método IMetaDataEmit::DefineTypeRefByName</span><span class="sxs-lookup"><span data-stu-id="4aba1-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="4aba1-103">Obtém um token de metadados para um tipo que é definido no escopo especificado, que está fora do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="4aba1-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aba1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4aba1-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aba1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4aba1-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="4aba1-106">no O token que especifica o escopo de resolução.</span><span class="sxs-lookup"><span data-stu-id="4aba1-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="4aba1-107">Os seguintes tipos de token são válidos:</span><span class="sxs-lookup"><span data-stu-id="4aba1-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="4aba1-108">`mdModuleRef`, se o tipo for definido no mesmo assembly no qual o chamador está definido.</span><span class="sxs-lookup"><span data-stu-id="4aba1-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="4aba1-109">`mdAssemblyRef`, se o tipo for definido em um assembly diferente daquele em que o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="4aba1-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="4aba1-110">`mdTypeRef`, se o tipo for um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="4aba1-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="4aba1-111">`mdModule`, se o tipo for definido no mesmo módulo no qual o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="4aba1-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="4aba1-112">NULL, se o tipo for definido globalmente.</span><span class="sxs-lookup"><span data-stu-id="4aba1-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="4aba1-113">no O nome do tipo de destino em Unicode.</span><span class="sxs-lookup"><span data-stu-id="4aba1-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="4aba1-114">fora Um ponteiro para o `mdTypeRef` token que é atribuído ao tipo.</span><span class="sxs-lookup"><span data-stu-id="4aba1-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aba1-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4aba1-115">Requirements</span></span>  
 <span data-ttu-id="4aba1-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aba1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aba1-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4aba1-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4aba1-118">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4aba1-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4aba1-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aba1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aba1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4aba1-120">See also</span></span>

- [<span data-ttu-id="4aba1-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4aba1-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4aba1-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4aba1-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
