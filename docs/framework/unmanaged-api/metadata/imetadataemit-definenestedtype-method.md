---
title: Método IMetaDataEmit::DefineNestedType
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0d105679a749b8c87099af871bdb42874d440b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446997"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="dd457-102">Método IMetaDataEmit::DefineNestedType</span><span class="sxs-lookup"><span data-stu-id="dd457-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="dd457-103">Cria a assinatura de metadados de uma definição de tipo, retorna um `mdTypeDef` para esse tipo de token e especifica que o tipo definido é um membro do tipo referenciado pelo `tdEncloser` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dd457-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd457-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd457-104">Syntax</span></span>  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd457-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd457-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="dd457-106">[in] O nome do tipo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="dd457-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="dd457-107">[in] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="dd457-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="dd457-108">Esse é um bitmask de `CorTypeAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="dd457-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="dd457-109">[in] O token de classe base.</span><span class="sxs-lookup"><span data-stu-id="dd457-109">[in] The token of the base class.</span></span> <span data-ttu-id="dd457-110">Isso é uma `mdTypeDef` ou um `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="dd457-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="dd457-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="dd457-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="dd457-112">[in] Uma matriz de tokens que especificam as interfaces que implementa essa interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="dd457-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="dd457-113">[in] O token do tipo delimitador.</span><span class="sxs-lookup"><span data-stu-id="dd457-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="dd457-114">O último elemento da matriz deve ser `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="dd457-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="dd457-115">[out] O `mdTypeDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="dd457-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd457-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd457-116">Requirements</span></span>  
 <span data-ttu-id="dd457-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd457-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd457-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd457-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd457-119">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="dd457-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd457-120">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd457-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd457-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd457-121">See Also</span></span>  
 [<span data-ttu-id="dd457-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="dd457-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="dd457-123">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="dd457-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
