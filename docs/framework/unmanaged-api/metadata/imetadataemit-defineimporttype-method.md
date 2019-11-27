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
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431843"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="9bf14-102">Método IMetaDataEmit::DefineImportType</span><span class="sxs-lookup"><span data-stu-id="9bf14-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="9bf14-103">Cria uma referência ao tipo especificado que é definido fora do escopo atual e define um token para essa referência.</span><span class="sxs-lookup"><span data-stu-id="9bf14-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bf14-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9bf14-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bf14-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="9bf14-106">no Uma interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) que representa o assembly do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="9bf14-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="9bf14-107">no Uma matriz que contém o hash para o assembly especificado por `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="9bf14-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="9bf14-108">no O número de bytes na matriz de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="9bf14-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="9bf14-109">no Uma interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa o escopo de metadados do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="9bf14-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="9bf14-110">no Um token `mdTypeDef` que especifica o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="9bf14-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="9bf14-111">no Uma interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) que representa o assembly no qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="9bf14-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="9bf14-112">fora O token de `mdTypeRef` que é definido no escopo atual para a referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="9bf14-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bf14-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bf14-113">Remarks</span></span>  
 <span data-ttu-id="9bf14-114">Antes de chamar o método [IMetaDataEmit::D efineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) , você pode usar o método `DefineImportType` para criar uma referência de tipo, no escopo atual, para a classe pai ou a interface pai do membro.</span><span class="sxs-lookup"><span data-stu-id="9bf14-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bf14-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9bf14-115">Requirements</span></span>  
 <span data-ttu-id="9bf14-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bf14-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bf14-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9bf14-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bf14-118">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9bf14-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bf14-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bf14-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf14-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bf14-120">See also</span></span>

- [<span data-ttu-id="9bf14-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9bf14-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9bf14-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9bf14-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
