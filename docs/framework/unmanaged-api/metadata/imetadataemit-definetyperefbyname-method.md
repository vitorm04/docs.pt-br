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
ms.openlocfilehash: 23a6931b31ea2d7e4e8d1cb3dc8adf3a51216315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175740"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="5b140-102">Método IMetaDataEmit::DefineTypeRefByName</span><span class="sxs-lookup"><span data-stu-id="5b140-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="5b140-103">Obtém um token de metadados para um tipo definido no escopo especificado, que está fora do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="5b140-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b140-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b140-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b140-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b140-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="5b140-106">[em] O token especificando o escopo de resolução.</span><span class="sxs-lookup"><span data-stu-id="5b140-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="5b140-107">Os seguintes tipos de tokens são válidos:</span><span class="sxs-lookup"><span data-stu-id="5b140-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="5b140-108">`mdModuleRef`, se o tipo for definido no mesmo conjunto em que o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="5b140-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5b140-109">`mdAssemblyRef`, se o tipo for definido em um conjunto diferente daquele em que o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="5b140-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5b140-110">`mdTypeRef`, se o tipo for um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="5b140-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="5b140-111">`mdModule`, se o tipo for definido no mesmo módulo em que o chamador é definido.</span><span class="sxs-lookup"><span data-stu-id="5b140-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5b140-112">Nulo, se o tipo for definido globalmente.</span><span class="sxs-lookup"><span data-stu-id="5b140-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="5b140-113">[em] O nome do tipo de destino em Unicode.</span><span class="sxs-lookup"><span data-stu-id="5b140-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="5b140-114">[fora] Um ponteiro `mdTypeRef` para o token atribuído ao tipo.</span><span class="sxs-lookup"><span data-stu-id="5b140-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b140-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b140-115">Requirements</span></span>  
 <span data-ttu-id="5b140-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b140-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b140-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5b140-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b140-118">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b140-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b140-119">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b140-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b140-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="5b140-120">See also</span></span>

- [<span data-ttu-id="5b140-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5b140-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5b140-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5b140-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
