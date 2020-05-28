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
ms.openlocfilehash: ec8a24251ac4f0701b1adab19829078270229ced
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004589"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="20aa6-102">Método IMetaDataEmit::DefineImportMember</span><span class="sxs-lookup"><span data-stu-id="20aa6-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="20aa6-103">Cria uma referência ao membro especificado de um tipo ou módulo que é definido fora do escopo atual e define um token para essa referência.</span><span class="sxs-lookup"><span data-stu-id="20aa6-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20aa6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20aa6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="20aa6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20aa6-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="20aa6-106">no Uma interface [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) que representa o assembly do qual o membro de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="20aa6-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="20aa6-107">no Uma matriz que contém o hash para o assembly especificado por `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="20aa6-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="20aa6-108">no O número de bytes na `pbHashValue` matriz.</span><span class="sxs-lookup"><span data-stu-id="20aa6-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="20aa6-109">no Uma interface [IMetaDataImport](imetadataimport-interface.md) que representa o escopo de metadados do qual o membro de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="20aa6-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="20aa6-110">no O token de metadados que especifica o membro de destino.</span><span class="sxs-lookup"><span data-stu-id="20aa6-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="20aa6-111">O token pode ser um `mdMethodDef` (para um método de membro), `mdProperty` (para uma propriedade de membro) ou um `mdFieldDef` token (para um campo de membro).</span><span class="sxs-lookup"><span data-stu-id="20aa6-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="20aa6-112">no Uma interface [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) que representa o assembly no qual o membro de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="20aa6-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="20aa6-113">no O `mdTypeRef` `mdModuleRef` token ou para o tipo ou módulo, respectivamente, que é proprietário do membro de destino.</span><span class="sxs-lookup"><span data-stu-id="20aa6-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="20aa6-114">fora O `mdMemberRef` token que é definido no escopo atual para a referência de membro.</span><span class="sxs-lookup"><span data-stu-id="20aa6-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20aa6-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="20aa6-115">Remarks</span></span>  
 <span data-ttu-id="20aa6-116">O `DefineImportMember` método pesquisa o membro, especificado por `mbMember` , que é definido em outro escopo, especificado por `pImport` e recupera suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="20aa6-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="20aa6-117">Ele usa essas informações para chamar o método [IMetaDataEmit::D efinememberref](imetadataemit-definememberref-method.md) no escopo atual para criar a referência de membro.</span><span class="sxs-lookup"><span data-stu-id="20aa6-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="20aa6-118">Em geral, antes de usar o `DefineImportMember` método, você deve criar, no escopo atual, uma referência de tipo ou referência de módulo para a classe pai, a interface ou o módulo do membro de destino.</span><span class="sxs-lookup"><span data-stu-id="20aa6-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="20aa6-119">O token de metadados para essa referência é passado no `tkParent` argumento.</span><span class="sxs-lookup"><span data-stu-id="20aa6-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="20aa6-120">Você não precisará criar uma referência para o pai do membro de destino se ele for resolvido posteriormente pelo compilador ou vinculador.</span><span class="sxs-lookup"><span data-stu-id="20aa6-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="20aa6-121">Para resumir:</span><span class="sxs-lookup"><span data-stu-id="20aa6-121">To summarize:</span></span>  
  
- <span data-ttu-id="20aa6-122">Se o membro de destino for um campo ou método, use o método [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md) para criar uma referência de tipo, no escopo atual, para a classe pai ou a interface pai do membro.</span><span class="sxs-lookup"><span data-stu-id="20aa6-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="20aa6-123">Se o membro de destino for uma variável global ou uma função global (ou seja, não for um membro de uma classe ou interface), use o método [IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md) para criar uma referência de módulo, no escopo atual, para o módulo pai do membro.</span><span class="sxs-lookup"><span data-stu-id="20aa6-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="20aa6-124">Se o pai do membro de destino for resolvido posteriormente pelo compilador ou vinculador, em seguida, `mdTokenNil` passe `tkParent` .</span><span class="sxs-lookup"><span data-stu-id="20aa6-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="20aa6-125">O único cenário no qual isso se aplica é quando uma função global ou uma variável global está sendo importada de um arquivo. obj que, por fim, será vinculado ao módulo atual e aos metadados mesclados.</span><span class="sxs-lookup"><span data-stu-id="20aa6-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20aa6-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20aa6-126">Requirements</span></span>  
 <span data-ttu-id="20aa6-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20aa6-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20aa6-128">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="20aa6-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20aa6-129">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20aa6-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20aa6-130">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20aa6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20aa6-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="20aa6-131">See also</span></span>

- [<span data-ttu-id="20aa6-132">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="20aa6-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="20aa6-133">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="20aa6-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
