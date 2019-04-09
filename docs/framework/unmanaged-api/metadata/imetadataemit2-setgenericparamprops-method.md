---
title: Método IMetaDataEmit2::SetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4daf24c1712b18d933da702e9e1ef1cbdbfc3639
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081899"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="0aefb-102">Método IMetaDataEmit2::SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="0aefb-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="0aefb-103">Define valores de propriedade para a definição de parâmetro genérico referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="0aefb-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aefb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0aefb-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aefb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0aefb-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="0aefb-106">[in] O token para a definição de parâmetro genérico para o qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="0aefb-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="0aefb-107">[in] Um valor igual a [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeração que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="0aefb-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="0aefb-108">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="0aefb-108">[in] Optional.</span></span> <span data-ttu-id="0aefb-109">O nome do parâmetro para o qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="0aefb-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="0aefb-110">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="0aefb-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="0aefb-111">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="0aefb-111">[in] Optional.</span></span> <span data-ttu-id="0aefb-112">Uma matriz terminada em zero de restrições de tipo.</span><span class="sxs-lookup"><span data-stu-id="0aefb-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="0aefb-113">Membros da matriz devem ser um `mdTypeDef`, `mdTypeRef`, ou `mdTypeSpec` token de metadados.</span><span class="sxs-lookup"><span data-stu-id="0aefb-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aefb-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0aefb-114">Requirements</span></span>  
 <span data-ttu-id="0aefb-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aefb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aefb-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0aefb-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0aefb-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0aefb-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0aefb-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0aefb-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0aefb-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0aefb-119">See also</span></span>

- [<span data-ttu-id="0aefb-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0aefb-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="0aefb-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0aefb-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
