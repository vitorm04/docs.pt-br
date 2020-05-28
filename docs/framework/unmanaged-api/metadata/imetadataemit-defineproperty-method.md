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
ms.openlocfilehash: 479cb25ad8e1c263d3539a4203ac5bea781eb931
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009366"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="0eb15-102">Método IMetaDataEmit::DefineProperty</span><span class="sxs-lookup"><span data-stu-id="0eb15-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="0eb15-103">Cria uma definição de propriedade para o tipo especificado, com os `get` `set` acessadores de método e especificados, e Obtém um token para essa definição de propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0eb15-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0eb15-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0eb15-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0eb15-106">no O token para a classe ou interface na qual a propriedade está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="0eb15-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="0eb15-107">no O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="0eb15-108">no Os sinalizadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="0eb15-109">no A assinatura da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="0eb15-110">no A contagem de bytes em `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="0eb15-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="0eb15-111">no O tipo do valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0eb15-112">no O valor padrão para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="0eb15-113">no A contagem de caracteres (Unicode) no `pValue` .</span><span class="sxs-lookup"><span data-stu-id="0eb15-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="0eb15-114">no O método que define o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="0eb15-115">no O método que obtém o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="0eb15-116">no Uma matriz de outros métodos associados à propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eb15-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="0eb15-117">Encerre a matriz com um `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="0eb15-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="0eb15-118">fora O `mdProperty` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="0eb15-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eb15-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0eb15-119">Requirements</span></span>  
 <span data-ttu-id="0eb15-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eb15-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb15-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0eb15-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0eb15-122">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0eb15-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eb15-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eb15-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb15-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="0eb15-124">See also</span></span>

- [<span data-ttu-id="0eb15-125">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0eb15-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0eb15-126">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0eb15-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
