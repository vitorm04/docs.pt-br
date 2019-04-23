---
title: Método IMetaDataEmit::SetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdee8491b22675fb8dd8fa89e77ebf8541185173
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207884"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="08f82-102">Método IMetaDataEmit::SetPropertyProps</span><span class="sxs-lookup"><span data-stu-id="08f82-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="08f82-103">Define os recursos armazenados nos metadados para uma propriedade definida por uma chamada anterior ao [método DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="08f82-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08f82-104">Syntax</span></span>  
  
```  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08f82-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08f82-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="08f82-106">[in] O token para a propriedade a ser alterada</span><span class="sxs-lookup"><span data-stu-id="08f82-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="08f82-107">[in] Sinalizadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="08f82-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="08f82-108">[in] O tipo de valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="08f82-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="08f82-109">[in] O valor padrão para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="08f82-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="08f82-110">[in] A contagem de (Unicode) caracteres em `pValue`.</span><span class="sxs-lookup"><span data-stu-id="08f82-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="08f82-111">[in] O método que define o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="08f82-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="08f82-112">[in] O método que obtém o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="08f82-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="08f82-113">[in] Uma matriz de outros métodos associado à propriedade.</span><span class="sxs-lookup"><span data-stu-id="08f82-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="08f82-114">Encerrar essa matriz com um `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="08f82-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08f82-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08f82-115">Requirements</span></span>  
 <span data-ttu-id="08f82-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f82-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f82-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08f82-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08f82-118">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="08f82-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08f82-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f82-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f82-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08f82-120">See also</span></span>

- [<span data-ttu-id="08f82-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="08f82-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="08f82-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="08f82-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
