---
title: Método IMetaDataAssemblyImport::EnumManifestResources
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176013"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="9bf7f-102">Método IMetaDataAssemblyImport::EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="9bf7f-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="9bf7f-103">Obtém um ponteiro para um enumerador para os recursos referenciados no manifesto de montagem atual.</span><span class="sxs-lookup"><span data-stu-id="9bf7f-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bf7f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="9bf7f-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bf7f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9bf7f-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="9bf7f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9bf7f-107">Este deve ser um `EnumManifestResources` valor nulo quando o método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="9bf7f-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="9bf7f-108">[fora] A matriz usada `mdManifestResource` para armazenar os tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="9bf7f-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9bf7f-109">[em] O número `mdManifestResource` máximo de tokens `rManifestResources`que podem ser colocados em .</span><span class="sxs-lookup"><span data-stu-id="9bf7f-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9bf7f-110">[fora] O número `mdManifestResource` de tokens `rManifestResources`realmente colocados em .</span><span class="sxs-lookup"><span data-stu-id="9bf7f-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bf7f-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9bf7f-111">Return Value</span></span>  
  
|<span data-ttu-id="9bf7f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bf7f-112">HRESULT</span></span>|<span data-ttu-id="9bf7f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bf7f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9bf7f-114">`EnumManifestResources`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="9bf7f-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9bf7f-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="9bf7f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="9bf7f-116">Neste caso, `pcTokens` está definido como zero.</span><span class="sxs-lookup"><span data-stu-id="9bf7f-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bf7f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bf7f-117">Requirements</span></span>  
 <span data-ttu-id="9bf7f-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bf7f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bf7f-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9bf7f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bf7f-120">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bf7f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9bf7f-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bf7f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf7f-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bf7f-122">See also</span></span>

- [<span data-ttu-id="9bf7f-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="9bf7f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
