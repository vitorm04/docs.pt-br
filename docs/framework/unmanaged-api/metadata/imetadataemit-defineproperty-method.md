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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c250a577f2ccdbbfefb35225b880c0e4317db36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448101"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="8b95b-102">Método IMetaDataEmit::DefineProperty</span><span class="sxs-lookup"><span data-stu-id="8b95b-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="8b95b-103">Cria uma definição de propriedade para o tipo especificado, com especificado `get` e `set` métodos acessadores e recebe um token para essa definição de propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b95b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b95b-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="8b95b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b95b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8b95b-106">[in] O token de classe ou interface na qual a propriedade está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="8b95b-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="8b95b-107">[in] O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="8b95b-108">[in] Os sinalizadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="8b95b-109">[in] A assinatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="8b95b-110">[in] A contagem de bytes em `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="8b95b-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="8b95b-111">[in] O tipo de valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8b95b-112">[in] O valor padrão para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="8b95b-113">[in] A contagem de (Unicode) caracteres `pValue`.</span><span class="sxs-lookup"><span data-stu-id="8b95b-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="8b95b-114">[in] O método que define o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="8b95b-115">[in] O método que obtém o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="8b95b-116">[in] Uma matriz de outros métodos associado à propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b95b-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="8b95b-117">Encerrar a matriz com um `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="8b95b-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="8b95b-118">[out] O `mdProperty` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="8b95b-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b95b-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b95b-119">Requirements</span></span>  
 <span data-ttu-id="8b95b-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b95b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b95b-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b95b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b95b-122">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8b95b-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b95b-123">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b95b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b95b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b95b-124">See Also</span></span>  
 [<span data-ttu-id="8b95b-125">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8b95b-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8b95b-126">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8b95b-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
