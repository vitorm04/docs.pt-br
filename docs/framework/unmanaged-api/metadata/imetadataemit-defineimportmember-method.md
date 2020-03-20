---
title: Método IMetaDataEmit::DefineImportMember
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175857"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="10e9f-102">Método IMetaDataEmit::DefineImportMember</span><span class="sxs-lookup"><span data-stu-id="10e9f-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="10e9f-103">Cria uma referência ao membro especificado de um tipo ou módulo definido fora do escopo atual e define um token para essa referência.</span><span class="sxs-lookup"><span data-stu-id="10e9f-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10e9f-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportMember (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,
    [in]  mdToken                  mbMember,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [in]  mdToken                  tkParent,
    [out] mdMemberRef              *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10e9f-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="10e9f-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="10e9f-106">[em] Uma interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) que representa o conjunto a partir do qual o membro-destino é importado.</span><span class="sxs-lookup"><span data-stu-id="10e9f-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="10e9f-107">[em] Uma matriz que contém o hash `pAssemImport`para a montagem especificada por .</span><span class="sxs-lookup"><span data-stu-id="10e9f-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="10e9f-108">[em] O número de bytes na `pbHashValue` matriz.</span><span class="sxs-lookup"><span data-stu-id="10e9f-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="10e9f-109">[em] Uma interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa o escopo de metadados do qual o membro-alvo é importado.</span><span class="sxs-lookup"><span data-stu-id="10e9f-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="10e9f-110">[em] O token de metadados que especifica o membro-alvo.</span><span class="sxs-lookup"><span data-stu-id="10e9f-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="10e9f-111">O token pode `mdMethodDef` ser um token (para um `mdProperty` `mdFieldDef` membro), (para uma propriedade de membro) ou (para um campo de membro).</span><span class="sxs-lookup"><span data-stu-id="10e9f-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="10e9f-112">[em] Uma interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) que representa o conjunto para o qual o membro-alvo é importado.</span><span class="sxs-lookup"><span data-stu-id="10e9f-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="10e9f-113">[em] O `mdTypeRef` `mdModuleRef` ou token para o tipo ou módulo, respectivamente, que possui o membro-alvo.</span><span class="sxs-lookup"><span data-stu-id="10e9f-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="10e9f-114">[fora] O `mdMemberRef` token definido no escopo atual para a referência do membro.</span><span class="sxs-lookup"><span data-stu-id="10e9f-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10e9f-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="10e9f-115">Remarks</span></span>  
 <span data-ttu-id="10e9f-116">O `DefineImportMember` método procura o membro, `mbMember`especificado por , que é `pImport`definido em outro escopo, especificado por , e recupera suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="10e9f-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="10e9f-117">Ele usa essas informações para chamar o método [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) no escopo atual para criar a referência do membro.</span><span class="sxs-lookup"><span data-stu-id="10e9f-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="10e9f-118">Geralmente, antes de `DefineImportMember` usar o método, você deve criar, no escopo atual, uma referência de tipo ou referência de módulo para a classe, interface ou módulo do membro-alvo.</span><span class="sxs-lookup"><span data-stu-id="10e9f-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="10e9f-119">O token de metadados para essa `tkParent` referência é então passado no argumento.</span><span class="sxs-lookup"><span data-stu-id="10e9f-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="10e9f-120">Você não precisa criar uma referência ao pai do membro-alvo se ele for resolvido posteriormente pelo compilador ou linker.</span><span class="sxs-lookup"><span data-stu-id="10e9f-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="10e9f-121">Resumidamente:</span><span class="sxs-lookup"><span data-stu-id="10e9f-121">To summarize:</span></span>  
  
- <span data-ttu-id="10e9f-122">Se o membro-alvo for um campo ou método, use o [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou o método [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) para criar uma referência de tipo, no escopo atual, para a classe pai do membro ou interface pai.</span><span class="sxs-lookup"><span data-stu-id="10e9f-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="10e9f-123">Se o membro-alvo for uma variável global ou função global (ou seja, não um membro de uma classe ou interface), use o método [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) para criar uma referência de módulo, no escopo atual, para o módulo pai do membro.</span><span class="sxs-lookup"><span data-stu-id="10e9f-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="10e9f-124">Se o pai do membro-alvo for resolvido posteriormente pelo compilador ou linker, então passe `mdTokenNil` para dentro `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="10e9f-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="10e9f-125">O único cenário em que isso se aplica é quando uma função global ou variável global está sendo importada de um arquivo .obj que será finalmente vinculado ao módulo atual e aos metadados mesclados.</span><span class="sxs-lookup"><span data-stu-id="10e9f-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10e9f-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10e9f-126">Requirements</span></span>  
 <span data-ttu-id="10e9f-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10e9f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10e9f-128">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="10e9f-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10e9f-129">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10e9f-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10e9f-130">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10e9f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e9f-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="10e9f-131">See also</span></span>

- [<span data-ttu-id="10e9f-132">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="10e9f-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="10e9f-133">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="10e9f-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
