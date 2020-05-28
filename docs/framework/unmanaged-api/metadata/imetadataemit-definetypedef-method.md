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
ms.openlocfilehash: dc064b00e32bb6b1d8c2d0c20f571b35919eae23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009334"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="378bd-102">Método IMetaDataEmit::DefineTypeDef</span><span class="sxs-lookup"><span data-stu-id="378bd-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="378bd-103">Cria uma definição de tipo para um tipo de Common Language Runtime e Obtém um token de metadados para essa definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="378bd-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="378bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="378bd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="378bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="378bd-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="378bd-106">no O nome do tipo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="378bd-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="378bd-107">[in] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="378bd-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="378bd-108">Esta é uma bitmask de `CoreTypeAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="378bd-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="378bd-109">no O token da classe base.</span><span class="sxs-lookup"><span data-stu-id="378bd-109">[in] The token of the base class.</span></span> <span data-ttu-id="378bd-110">Ele deve ser um `mdTypeDef` ou um `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="378bd-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="378bd-111">no Uma matriz de tokens que especifica as interfaces que essa classe ou interface implementa.</span><span class="sxs-lookup"><span data-stu-id="378bd-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="378bd-112">fora O `mdTypeDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="378bd-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="378bd-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="378bd-113">Remarks</span></span>  
 <span data-ttu-id="378bd-114">Um sinalizador em `dwTypeDefFlags` especifica se o tipo que está sendo criado é um tipo de referência de Common Type System (classe ou interface) ou um tipo de valor de Common Type System.</span><span class="sxs-lookup"><span data-stu-id="378bd-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="378bd-115">Dependendo dos parâmetros fornecidos, esse método, como um efeito colateral, também pode criar um `mdInterfaceImpl` registro para cada interface herdada ou implementada por esse tipo.</span><span class="sxs-lookup"><span data-stu-id="378bd-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="378bd-116">No entanto, esse método não retorna nenhum desses `mdInterfaceImpl` tokens.</span><span class="sxs-lookup"><span data-stu-id="378bd-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="378bd-117">Se um cliente quiser adicionar ou modificar um token posteriormente `mdInterfaceImpl` , ele deverá usar a `IMetaDataImport` interface para enumerá-los.</span><span class="sxs-lookup"><span data-stu-id="378bd-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="378bd-118">Se você quiser usar a semântica COM da `[default]` interface, deverá fornecer a interface padrão como o primeiro elemento em `rtkImplements` ; um atributo personalizado definido na classe indicará que a classe tem uma interface padrão (que sempre é considerada o primeiro `mdInterfaceImpl` token declarado para a classe).</span><span class="sxs-lookup"><span data-stu-id="378bd-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="378bd-119">Cada elemento da `rtkImplements` matriz contém um `mdTypeDef` token ou `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="378bd-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="378bd-120">O último elemento na matriz deve ser `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="378bd-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="378bd-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="378bd-121">Requirements</span></span>  
 <span data-ttu-id="378bd-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="378bd-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="378bd-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="378bd-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="378bd-124">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="378bd-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="378bd-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="378bd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378bd-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="378bd-126">See also</span></span>

- [<span data-ttu-id="378bd-127">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="378bd-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="378bd-128">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="378bd-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
