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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177687"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="5a986-102">Método IMetaDataEmit::DefineImportType</span><span class="sxs-lookup"><span data-stu-id="5a986-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="5a986-103">Cria uma referência ao tipo especificado definido fora do escopo atual e define um token para essa referência.</span><span class="sxs-lookup"><span data-stu-id="5a986-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a986-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a986-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="5a986-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a986-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="5a986-106">[em] Uma interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) que representa o conjunto a partir do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="5a986-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="5a986-107">[em] Uma matriz que contém o hash `pAssemImport`para a montagem especificada por .</span><span class="sxs-lookup"><span data-stu-id="5a986-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="5a986-108">[em] O número de bytes na `pbHashValue` matriz.</span><span class="sxs-lookup"><span data-stu-id="5a986-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="5a986-109">[em] Uma interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa o escopo de metadados a partir do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="5a986-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="5a986-110">[em] Um `mdTypeDef` token que especifica o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="5a986-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="5a986-111">[em] Uma interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) que representa o conjunto no qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="5a986-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="5a986-112">[fora] O `mdTypeRef` token definido no escopo atual para a referência do tipo.</span><span class="sxs-lookup"><span data-stu-id="5a986-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a986-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a986-113">Remarks</span></span>  
 <span data-ttu-id="5a986-114">Antes de chamar o método [IMetaDataEmit::DefineImportMember,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) você pode usar o `DefineImportType` método para criar uma referência de tipo, no escopo atual, para a classe pai do membro ou interface pai.</span><span class="sxs-lookup"><span data-stu-id="5a986-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a986-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a986-115">Requirements</span></span>  
 <span data-ttu-id="5a986-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a986-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a986-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5a986-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a986-118">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a986-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a986-119">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a986-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a986-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="5a986-120">See also</span></span>

- [<span data-ttu-id="5a986-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5a986-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5a986-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5a986-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
