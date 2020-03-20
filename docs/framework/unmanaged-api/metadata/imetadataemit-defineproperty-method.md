---
title: Método IMetaDataEmit::DefineProperty
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175779"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="f2b56-102">Método IMetaDataEmit::DefineProperty</span><span class="sxs-lookup"><span data-stu-id="f2b56-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="f2b56-103">Cria uma definição de propriedade para o `get` tipo `set` especificado, com os acessórios especificados e do método, e recebe um token para essa definição de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b56-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2b56-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2b56-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2b56-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f2b56-106">[em] O token para classe ou interface na qual a propriedade está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="f2b56-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="f2b56-107">[em] O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="f2b56-108">[em] As bandeiras da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="f2b56-109">[em] A assinatura da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="f2b56-110">[em] A contagem de `pvSig`bytes em .</span><span class="sxs-lookup"><span data-stu-id="f2b56-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="f2b56-111">[em] O tipo de valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f2b56-112">[em] O valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="f2b56-113">[em] A contagem de caracteres `pValue`(Unicode) em .</span><span class="sxs-lookup"><span data-stu-id="f2b56-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="f2b56-114">[em] O método que define o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="f2b56-115">[em] O método que obtém o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="f2b56-116">[em] Uma série de outros métodos associados à propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2b56-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="f2b56-117">Termine a matriz `mdTokenNil`com um .</span><span class="sxs-lookup"><span data-stu-id="f2b56-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="f2b56-118">[fora] O `mdProperty` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="f2b56-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2b56-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2b56-119">Requirements</span></span>  
 <span data-ttu-id="f2b56-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b56-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b56-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2b56-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2b56-122">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2b56-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2b56-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b56-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b56-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="f2b56-124">See also</span></span>

- [<span data-ttu-id="f2b56-125">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f2b56-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f2b56-126">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f2b56-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
