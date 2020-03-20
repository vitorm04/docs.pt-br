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
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175805"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="c3f72-102">Método IMetaDataEmit::DefineNestedType</span><span class="sxs-lookup"><span data-stu-id="c3f72-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="c3f72-103">Cria a assinatura de metadados de `mdTypeDef` uma definição de tipo, retorna um token para esse tipo `tdEncloser` e especifica que o tipo definido é um membro do tipo referenciado pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c3f72-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3f72-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f72-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3f72-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="c3f72-106">[em] O nome do tipo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="c3f72-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="c3f72-107">[em] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="c3f72-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="c3f72-108">Isto é uma `CorTypeAttr` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="c3f72-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="c3f72-109">[em] O símbolo da classe base.</span><span class="sxs-lookup"><span data-stu-id="c3f72-109">[in] The token of the base class.</span></span> <span data-ttu-id="c3f72-110">Isso é `mdTypeDef` um `mdTypeRef` ou um símbolo.</span><span class="sxs-lookup"><span data-stu-id="c3f72-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="c3f72-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="c3f72-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="c3f72-112">[em] Uma matriz de tokens que especificam as interfaces que esta classe ou interface implementa.</span><span class="sxs-lookup"><span data-stu-id="c3f72-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="c3f72-113">[em] O símbolo do tipo de fechamento.</span><span class="sxs-lookup"><span data-stu-id="c3f72-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="c3f72-114">O último elemento da `mdTokenNil`matriz deve ser .</span><span class="sxs-lookup"><span data-stu-id="c3f72-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="c3f72-115">[fora] O `mdTypeDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="c3f72-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f72-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3f72-116">Requirements</span></span>  
 <span data-ttu-id="c3f72-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f72-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f72-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3f72-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3f72-119">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3f72-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3f72-120">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f72-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f72-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3f72-121">See also</span></span>

- [<span data-ttu-id="c3f72-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c3f72-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c3f72-123">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c3f72-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
