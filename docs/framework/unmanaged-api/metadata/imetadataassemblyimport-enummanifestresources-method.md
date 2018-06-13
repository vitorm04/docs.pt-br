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
ms.openlocfilehash: 707e482a6952ee1266950dc181fbc85e5d6ef398
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448049"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="bcc3f-102">Método IMetaDataAssemblyImport::EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="bcc3f-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="bcc3f-103">Obtém um ponteiro para um enumerador para os recursos referenciados no manifesto do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcc3f-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcc3f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bcc3f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bcc3f-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bcc3f-107">Isso deve ser nulo quando o `EnumManifestResources` método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="bcc3f-108">[out] A matriz usada para armazenar o `mdManifestResource` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bcc3f-109">[in] O número máximo de `mdManifestResource` tokens que podem ser colocados em `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bcc3f-110">[out] O número de `mdManifestResource` tokens realmente realizada em `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bcc3f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bcc3f-111">Return Value</span></span>  
  
|<span data-ttu-id="bcc3f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bcc3f-112">HRESULT</span></span>|<span data-ttu-id="bcc3f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcc3f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bcc3f-114">`EnumManifestResources` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bcc3f-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bcc3f-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="bcc3f-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bcc3f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bcc3f-117">Requirements</span></span>  
 <span data-ttu-id="bcc3f-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcc3f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc3f-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bcc3f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bcc3f-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bcc3f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bcc3f-121">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcc3f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc3f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcc3f-122">See Also</span></span>  
 [<span data-ttu-id="bcc3f-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="bcc3f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
