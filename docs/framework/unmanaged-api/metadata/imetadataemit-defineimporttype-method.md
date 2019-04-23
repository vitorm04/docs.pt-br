---
title: Método IMetaDataEmit::DefineImportType
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9debf041a26af128dea3cde214630f5a95eac71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090648"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="f1175-102">Método IMetaDataEmit::DefineImportType</span><span class="sxs-lookup"><span data-stu-id="f1175-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="f1175-103">Cria uma referência ao tipo especificado que é definido fora do escopo atual e define um token para essa referência.</span><span class="sxs-lookup"><span data-stu-id="f1175-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1175-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1175-104">Syntax</span></span>  
  
```  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1175-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1175-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="f1175-106">[in] Uma [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface que representa o assembly do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="f1175-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f1175-107">[in] Uma matriz que contém o hash do assembly especificado por `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="f1175-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f1175-108">[in] O número de bytes no `pbHashValue` matriz.</span><span class="sxs-lookup"><span data-stu-id="f1175-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="f1175-109">[in] Uma [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface que representa o escopo de metadados do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="f1175-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="f1175-110">[in] Um `mdTypeDef` token que especifica o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="f1175-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="f1175-111">[in] Uma [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface que representa o assembly para o qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="f1175-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f1175-112">[out] O `mdTypeRef` token que é definido no escopo atual para a referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="f1175-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1175-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1175-113">Remarks</span></span>  
 <span data-ttu-id="f1175-114">Antes de chamar o [imetadataemit:: Defineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) método, você pode usar o `DefineImportType` método para criar uma referência de tipo no escopo atual para a classe pai ou a interface pai do membro.</span><span class="sxs-lookup"><span data-stu-id="f1175-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1175-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1175-115">Requirements</span></span>  
 <span data-ttu-id="f1175-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1175-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1175-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1175-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1175-118">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f1175-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1175-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1175-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1175-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1175-120">See also</span></span>

- [<span data-ttu-id="f1175-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f1175-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f1175-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f1175-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
