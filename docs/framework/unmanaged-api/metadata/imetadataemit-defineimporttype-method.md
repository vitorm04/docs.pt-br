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
ms.openlocfilehash: 68e6f7599db55ed9429f159b380a8a9f8ae3f034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447480"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="77153-102">Método IMetaDataEmit::DefineImportType</span><span class="sxs-lookup"><span data-stu-id="77153-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="77153-103">Cria uma referência para o tipo especificado que está definido fora do escopo atual e define um token para essa referência.</span><span class="sxs-lookup"><span data-stu-id="77153-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77153-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77153-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="77153-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77153-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="77153-106">[in] Um [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface que representa o assembly do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="77153-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="77153-107">[in] Uma matriz que contém o hash para o conjunto especificado por `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="77153-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="77153-108">[in] O número de bytes a `pbHashValue` matriz.</span><span class="sxs-lookup"><span data-stu-id="77153-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="77153-109">[in] Um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface que representa o escopo de metadados do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="77153-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="77153-110">[in] Um `mdTypeDef` token que especifica o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="77153-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="77153-111">[in] Um [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface que representa o assembly para o qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="77153-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="77153-112">[out] O `mdTypeRef` token que é definido no escopo atual para a referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="77153-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77153-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="77153-113">Remarks</span></span>  
 <span data-ttu-id="77153-114">Antes de chamar o [: Defineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) método, você pode usar o `DefineImportType` método para criar uma referência de tipo, no escopo atual para a classe pai ou a interface pai do membro.</span><span class="sxs-lookup"><span data-stu-id="77153-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77153-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77153-115">Requirements</span></span>  
 <span data-ttu-id="77153-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77153-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77153-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="77153-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77153-118">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="77153-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77153-119">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77153-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77153-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77153-120">See Also</span></span>  
 [<span data-ttu-id="77153-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="77153-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="77153-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="77153-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
