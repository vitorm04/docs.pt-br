---
title: Método IMetaDataEmit::DefineTypeDef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf2ca9719cdf62637292bdb39437d36f4b3fcd49
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494396"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="b8efc-102">Método IMetaDataEmit::DefineTypeDef</span><span class="sxs-lookup"><span data-stu-id="b8efc-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="b8efc-103">Cria uma definição de tipo para um tipo common language runtime e obtém um token de metadados para essa definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="b8efc-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8efc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8efc-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8efc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8efc-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="b8efc-106">[in] O nome do tipo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="b8efc-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="b8efc-107">[in] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="b8efc-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="b8efc-108">Esse é um bitmask de `CoreTypeAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="b8efc-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="b8efc-109">[in] O token da classe base.</span><span class="sxs-lookup"><span data-stu-id="b8efc-109">[in] The token of the base class.</span></span> <span data-ttu-id="b8efc-110">Ele deve ser um `mdTypeDef` ou um `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="b8efc-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="b8efc-111">[in] Uma matriz de tokens especificando as interfaces que implementa essa interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="b8efc-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="b8efc-112">[out] O `mdTypeDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="b8efc-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8efc-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8efc-113">Remarks</span></span>  
 <span data-ttu-id="b8efc-114">Um sinalizador no `dwTypeDefFlags` Especifica se o tipo que está sendo criado é um tipo sistema referência tipo comum (classe ou interface) ou um tipo de valor de sistema de tipo comum.</span><span class="sxs-lookup"><span data-stu-id="b8efc-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="b8efc-115">Dependendo dos parâmetros fornecidos, esse método, como um efeito colateral, também pode criar um `mdInterfaceImpl` registros para cada interface que é herdada ou implementada por esse tipo.</span><span class="sxs-lookup"><span data-stu-id="b8efc-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="b8efc-116">No entanto, esse método não retorna qualquer um desses `mdInterfaceImpl` tokens.</span><span class="sxs-lookup"><span data-stu-id="b8efc-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="b8efc-117">Se um cliente deseja posteriormente, adicionar ou modificar uma `mdInterfaceImpl` token, ele deve usar o `IMetaDataImport` interface para enumerá-los.</span><span class="sxs-lookup"><span data-stu-id="b8efc-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="b8efc-118">Se você quiser usar semântica COM do `[default]` interface, você deve fornecer a interface padrão como o primeiro elemento no `rtkImplements`; um atributo personalizado definido na classe indicará que a classe tem uma interface padrão (que é sempre considerado como o primeiro `mdInterfaceImpl` token declarado para a classe).</span><span class="sxs-lookup"><span data-stu-id="b8efc-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="b8efc-119">Cada elemento do `rtkImplements` matriz mantém uma `mdTypeDef` ou `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="b8efc-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="b8efc-120">O último elemento na matriz deve ser `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="b8efc-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8efc-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8efc-121">Requirements</span></span>  
 <span data-ttu-id="b8efc-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8efc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8efc-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8efc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8efc-124">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b8efc-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8efc-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8efc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8efc-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8efc-126">See also</span></span>
- [<span data-ttu-id="b8efc-127">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b8efc-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b8efc-128">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b8efc-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
