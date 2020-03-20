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
ms.openlocfilehash: fd7f149e806727d849cdceb3ffbc5dc7392fcf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177405"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="70443-102">Método IMetaDataEmit2::SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="70443-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="70443-103">Define valores de propriedade para a definição de parâmetro genérico referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="70443-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70443-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70443-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70443-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="70443-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="70443-106">[em] O token para a definição de parâmetro genérico para o qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="70443-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="70443-107">[em] Um valor da enumeração [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="70443-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="70443-108">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="70443-108">[in] Optional.</span></span> <span data-ttu-id="70443-109">O nome do parâmetro para o qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="70443-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="70443-110">[em] Reservado para a extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="70443-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="70443-111">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="70443-111">[in] Optional.</span></span> <span data-ttu-id="70443-112">Uma matriz de restrições de tipo com término zero.</span><span class="sxs-lookup"><span data-stu-id="70443-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="70443-113">Os membros da `mdTypeDef` `mdTypeRef`matriz `mdTypeSpec` devem ser um token de metadados ou de metadados.</span><span class="sxs-lookup"><span data-stu-id="70443-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70443-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70443-114">Requirements</span></span>  
 <span data-ttu-id="70443-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70443-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70443-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70443-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70443-117">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70443-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70443-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70443-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70443-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="70443-119">See also</span></span>

- [<span data-ttu-id="70443-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="70443-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="70443-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="70443-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
