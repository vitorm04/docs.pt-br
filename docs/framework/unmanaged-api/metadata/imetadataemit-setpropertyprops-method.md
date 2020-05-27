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
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007774"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="35bf5-102">Método IMetaDataEmit::SetPropertyProps</span><span class="sxs-lookup"><span data-stu-id="35bf5-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="35bf5-103">Define os recursos armazenados em metadados para uma propriedade definida por uma chamada anterior para o [método definoproperty](imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="35bf5-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35bf5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35bf5-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="35bf5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35bf5-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="35bf5-106">no O token para a propriedade a ser alterada</span><span class="sxs-lookup"><span data-stu-id="35bf5-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="35bf5-107">no Sinalizadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="35bf5-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="35bf5-108">no O tipo do valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="35bf5-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="35bf5-109">no O valor padrão para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="35bf5-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="35bf5-110">no A contagem de caracteres (Unicode) no `pValue` .</span><span class="sxs-lookup"><span data-stu-id="35bf5-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="35bf5-111">no O método que define o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="35bf5-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="35bf5-112">no O método que obtém o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="35bf5-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="35bf5-113">no Uma matriz de outros métodos associados à propriedade.</span><span class="sxs-lookup"><span data-stu-id="35bf5-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="35bf5-114">Terminar esta matriz com um `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="35bf5-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35bf5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35bf5-115">Requirements</span></span>  
 <span data-ttu-id="35bf5-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35bf5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35bf5-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="35bf5-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="35bf5-118">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="35bf5-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35bf5-119">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35bf5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35bf5-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="35bf5-120">See also</span></span>

- [<span data-ttu-id="35bf5-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="35bf5-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="35bf5-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="35bf5-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
