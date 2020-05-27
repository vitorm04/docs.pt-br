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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004680"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="9730a-102">Método IMetaDataEmit::DefineImportType</span><span class="sxs-lookup"><span data-stu-id="9730a-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="9730a-103">Cria uma referência ao tipo especificado que é definido fora do escopo atual e define um token para essa referência.</span><span class="sxs-lookup"><span data-stu-id="9730a-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9730a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9730a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9730a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9730a-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="9730a-106">no Uma interface [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) que representa o assembly do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="9730a-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="9730a-107">no Uma matriz que contém o hash para o assembly especificado por `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="9730a-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="9730a-108">no O número de bytes na `pbHashValue` matriz.</span><span class="sxs-lookup"><span data-stu-id="9730a-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="9730a-109">no Uma interface [IMetaDataImport](imetadataimport-interface.md) que representa o escopo de metadados do qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="9730a-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="9730a-110">no Um `mdTypeDef` token que especifica o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="9730a-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="9730a-111">no Uma interface [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) que representa o assembly no qual o tipo de destino é importado.</span><span class="sxs-lookup"><span data-stu-id="9730a-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="9730a-112">fora O `mdTypeRef` token que é definido no escopo atual para a referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="9730a-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9730a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9730a-113">Remarks</span></span>  
 <span data-ttu-id="9730a-114">Antes de chamar o método [IMetaDataEmit::D efineimportmember](imetadataemit-defineimportmember-method.md) , você pode usar o `DefineImportType` método para criar uma referência de tipo, no escopo atual, para a classe pai ou a interface pai do membro.</span><span class="sxs-lookup"><span data-stu-id="9730a-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9730a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9730a-115">Requirements</span></span>  
 <span data-ttu-id="9730a-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9730a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9730a-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9730a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9730a-118">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9730a-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9730a-119">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9730a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9730a-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="9730a-120">See also</span></span>

- [<span data-ttu-id="9730a-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9730a-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9730a-122">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9730a-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
