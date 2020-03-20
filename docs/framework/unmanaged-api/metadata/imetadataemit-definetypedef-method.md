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
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175753"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="a7330-102">Método IMetaDataEmit::DefineTypeDef</span><span class="sxs-lookup"><span data-stu-id="a7330-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="a7330-103">Cria uma definição de tipo para um tipo de tempo de execução de idioma comum e obtém um token de metadados para essa definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="a7330-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7330-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7330-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7330-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7330-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="a7330-106">[em] O nome do tipo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="a7330-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="a7330-107">[em] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="a7330-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="a7330-108">Isto é uma `CoreTypeAttr` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="a7330-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="a7330-109">[em] O símbolo da classe base.</span><span class="sxs-lookup"><span data-stu-id="a7330-109">[in] The token of the base class.</span></span> <span data-ttu-id="a7330-110">Deve ser um `mdTypeDef` ou `mdTypeRef` um símbolo.</span><span class="sxs-lookup"><span data-stu-id="a7330-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="a7330-111">[em] Uma matriz de tokens especificando as interfaces que esta classe ou interface implementa.</span><span class="sxs-lookup"><span data-stu-id="a7330-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="a7330-112">[fora] O `mdTypeDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="a7330-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7330-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7330-113">Remarks</span></span>  
 <span data-ttu-id="a7330-114">Um sinalizador `dwTypeDefFlags` em especifica se o tipo que está sendo criado é um tipo de referência de sistema de tipo comum (classe ou interface) ou um tipo de valor de tipo comum.</span><span class="sxs-lookup"><span data-stu-id="a7330-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="a7330-115">Dependendo dos parâmetros fornecidos, este método, como `mdInterfaceImpl` efeito colateral, também pode criar um registro para cada interface herdada ou implementada por esse tipo.</span><span class="sxs-lookup"><span data-stu-id="a7330-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="a7330-116">No entanto, este método `mdInterfaceImpl` não retorna nenhum desses tokens.</span><span class="sxs-lookup"><span data-stu-id="a7330-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="a7330-117">Se um cliente quiser adicionar `mdInterfaceImpl` ou modificar um token posteriormente, ele deve usar a `IMetaDataImport` interface para enumera-los.</span><span class="sxs-lookup"><span data-stu-id="a7330-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="a7330-118">Se você quiser usar a semântica COM da `[default]` interface, você `rtkImplements`deve fornecer a interface padrão como o primeiro elemento em ; um atributo personalizado definido na classe indicará que a classe tem uma `mdInterfaceImpl` interface padrão (que é sempre assumida como o primeiro token declarado para a classe).</span><span class="sxs-lookup"><span data-stu-id="a7330-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="a7330-119">Cada elemento `rtkImplements` da matriz `mdTypeDef` `mdTypeRef` contém um ou token.</span><span class="sxs-lookup"><span data-stu-id="a7330-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="a7330-120">O último elemento na `mdTokenNil`matriz deve ser .</span><span class="sxs-lookup"><span data-stu-id="a7330-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7330-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7330-121">Requirements</span></span>  
 <span data-ttu-id="a7330-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7330-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7330-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7330-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7330-124">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7330-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7330-125">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7330-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7330-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="a7330-126">See also</span></span>

- [<span data-ttu-id="a7330-127">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a7330-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a7330-128">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a7330-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
