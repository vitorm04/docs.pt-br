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
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492727"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="015f2-102">Método IMetaDataEmit2::SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="015f2-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="015f2-103">Define valores de propriedade para a definição de parâmetro genérico referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="015f2-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="015f2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="015f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="015f2-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="015f2-106">no O token para a definição de parâmetro genérico para a qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="015f2-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="015f2-107">no Um valor da enumeração [CorGenericParamAttr](corgenericparamattr-enumeration.md) que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="015f2-107">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="015f2-108">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="015f2-108">[in] Optional.</span></span> <span data-ttu-id="015f2-109">O nome do parâmetro para o qual definir valores.</span><span class="sxs-lookup"><span data-stu-id="015f2-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="015f2-110">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="015f2-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="015f2-111">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="015f2-111">[in] Optional.</span></span> <span data-ttu-id="015f2-112">Uma matriz de restrições de tipo terminada em zero.</span><span class="sxs-lookup"><span data-stu-id="015f2-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="015f2-113">Os membros da matriz devem ser um `mdTypeDef` `mdTypeRef` token de metadados, ou `mdTypeSpec` .</span><span class="sxs-lookup"><span data-stu-id="015f2-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="015f2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="015f2-114">Requirements</span></span>  
 <span data-ttu-id="015f2-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="015f2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="015f2-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="015f2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="015f2-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="015f2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="015f2-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="015f2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015f2-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="015f2-119">See also</span></span>

- [<span data-ttu-id="015f2-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="015f2-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="015f2-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="015f2-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
