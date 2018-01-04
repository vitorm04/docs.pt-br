---
title: "Método IMetaDataEmit::DefineImportMember"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineImportMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bbe2c3144372ba66a0b3bad6198aefeeb7e12d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="01589-102">Método IMetaDataEmit::DefineImportMember</span><span class="sxs-lookup"><span data-stu-id="01589-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="01589-103">Cria uma referência ao membro de um módulo que está definido fora do escopo atual e define um token para essa referência ou tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="01589-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01589-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01589-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="01589-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01589-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="01589-106">[in] Um [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface que representa o assembly do qual o membro de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="01589-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="01589-107">[in] Uma matriz que contém o hash para o conjunto especificado por `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="01589-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="01589-108">[in] O número de bytes a `pbHashValue` matriz.</span><span class="sxs-lookup"><span data-stu-id="01589-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="01589-109">[in] Um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface que representa o escopo de metadados do qual o membro de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="01589-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="01589-110">[in] O token de metadados que especifica o membro de destino.</span><span class="sxs-lookup"><span data-stu-id="01589-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="01589-111">O token pode ser um `mdMethodDef` (para um método de membro) `mdProperty` (para uma propriedade de membro), ou `mdFieldDef` (para um campo de membro) token.</span><span class="sxs-lookup"><span data-stu-id="01589-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="01589-112">[in] Um [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface que representa o assembly para o qual o membro de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="01589-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="01589-113">[in] O `mdTypeRef` ou `mdModuleRef` token para o tipo ou módulo, respectivamente, que possui o membro de destino.</span><span class="sxs-lookup"><span data-stu-id="01589-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="01589-114">[out] O `mdMemberRef` token que é definido no escopo atual para a referência do membro.</span><span class="sxs-lookup"><span data-stu-id="01589-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01589-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="01589-115">Remarks</span></span>  
 <span data-ttu-id="01589-116">O `DefineImportMember` método procura o membro especificado por `mbMember`, que é definido em outro escopo, especificado por `pImport`e recuperar suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="01589-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="01589-117">Ele usa essas informações para chamar o [: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) método no escopo atual para criar a referência do membro.</span><span class="sxs-lookup"><span data-stu-id="01589-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="01589-118">Em geral, antes de usar o `DefineImportMember` método, você deve criar, no escopo atual, uma referência de tipo ou a referência de módulo para o módulo, interface ou classe pai do membro de destino.</span><span class="sxs-lookup"><span data-stu-id="01589-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="01589-119">O token de metadados para essa referência, em seguida, é passado a `tkParent` argumento.</span><span class="sxs-lookup"><span data-stu-id="01589-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="01589-120">Você não precisa criar uma referência ao pai do membro de destino se ele será resolvido posteriormente pelo compilador ou vinculador.</span><span class="sxs-lookup"><span data-stu-id="01589-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="01589-121">Para resumir:</span><span class="sxs-lookup"><span data-stu-id="01589-121">To summarize:</span></span>  
  
-   <span data-ttu-id="01589-122">Se o membro de destino é um campo ou método, use o [Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) método para criar uma referência de tipo, no escopo atual, para o a classe pai ou interface pai do membro.</span><span class="sxs-lookup"><span data-stu-id="01589-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
-   <span data-ttu-id="01589-123">Se o membro de destino for uma variável ou global função global (ou seja, não um membro de uma classe ou interface), use o [Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) método para criar uma referência de módulo, no escopo atual para o pai do membro módulo.</span><span class="sxs-lookup"><span data-stu-id="01589-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
-   <span data-ttu-id="01589-124">Se o pai do membro de destino será resolvido posteriormente pelo compilador ou vinculador, passe `mdTokenNil` em `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="01589-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="01589-125">O único cenário em que isso se aplica é quando uma função global ou variável global que está sendo importada de um arquivo. obj, por fim, será vinculado no módulo atual e os metadados de mesclagem.</span><span class="sxs-lookup"><span data-stu-id="01589-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01589-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01589-126">Requirements</span></span>  
 <span data-ttu-id="01589-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01589-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01589-128">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01589-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01589-129">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="01589-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01589-130">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01589-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01589-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01589-131">See Also</span></span>  
 [<span data-ttu-id="01589-132">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="01589-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="01589-133">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="01589-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
