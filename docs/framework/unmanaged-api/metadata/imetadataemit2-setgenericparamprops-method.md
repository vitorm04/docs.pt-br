---
title: "Método IMetaDataEmit2::SetGenericParamProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SetGenericParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5de54b3d113c8d43bd004b18e0a6cb22b1051dc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="aa09d-102">Método IMetaDataEmit2::SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="aa09d-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="aa09d-103">Define valores de propriedade para a definição de parâmetro genérico referenciado por token especificado.</span><span class="sxs-lookup"><span data-stu-id="aa09d-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa09d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa09d-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa09d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa09d-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="aa09d-106">[in] O token para a definição de parâmetro genérico para o qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="aa09d-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="aa09d-107">[in] Um valor de [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeração que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="aa09d-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="aa09d-108">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="aa09d-108">[in] Optional.</span></span> <span data-ttu-id="aa09d-109">O nome do parâmetro para o qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="aa09d-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="aa09d-110">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="aa09d-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="aa09d-111">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="aa09d-111">[in] Optional.</span></span> <span data-ttu-id="aa09d-112">Uma matriz de restrições de tipo terminada em zero.</span><span class="sxs-lookup"><span data-stu-id="aa09d-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="aa09d-113">Membros da matriz devem ser um `mdTypeDef`, `mdTypeRef`, ou `mdTypeSpec` token de metadados.</span><span class="sxs-lookup"><span data-stu-id="aa09d-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa09d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa09d-114">Requirements</span></span>  
 <span data-ttu-id="aa09d-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa09d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa09d-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa09d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa09d-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="aa09d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa09d-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa09d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa09d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa09d-119">See Also</span></span>  
 [<span data-ttu-id="aa09d-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="aa09d-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="aa09d-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="aa09d-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
