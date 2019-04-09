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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7abcb7b69d0f0f2c53cd236c9b4092a94e0f421c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110671"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="3e575-102">Método IMetaDataAssemblyImport::EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="3e575-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="3e575-103">Obtém um ponteiro para um enumerador para os recursos referenciados no manifesto do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="3e575-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e575-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e575-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="3e575-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e575-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3e575-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="3e575-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3e575-107">Isso deve ser um null valor quando o `EnumManifestResources` método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="3e575-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="3e575-108">[out] A matriz usada para armazenar o `mdManifestResource` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="3e575-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3e575-109">[in] O número máximo de `mdManifestResource` tokens que podem ser colocadas em `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="3e575-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3e575-110">[out] O número de `mdManifestResource` tokens realmente colocados nos `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="3e575-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e575-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3e575-111">Return Value</span></span>  
  
|<span data-ttu-id="3e575-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e575-112">HRESULT</span></span>|<span data-ttu-id="3e575-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e575-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources` <span data-ttu-id="3e575-114">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e575-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3e575-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="3e575-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3e575-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="3e575-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e575-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e575-117">Requirements</span></span>  
 <span data-ttu-id="3e575-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e575-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e575-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3e575-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e575-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3e575-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3e575-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3e575-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3e575-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e575-122">See also</span></span>

- [<span data-ttu-id="3e575-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="3e575-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
