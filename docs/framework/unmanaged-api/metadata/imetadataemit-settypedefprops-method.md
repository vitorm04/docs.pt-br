---
title: Método IMetaDataEmit::SetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 3ab29fc8c983b354ad5088d26c547868940ec70a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447723"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="f3219-102">Método IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="f3219-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="f3219-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="f3219-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3219-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3219-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3219-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3219-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f3219-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="f3219-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="f3219-107">[in] `TypeDef` attributes.</span><span class="sxs-lookup"><span data-stu-id="f3219-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="f3219-108">This is a bitmask of `CorTypeAttr` values.</span><span class="sxs-lookup"><span data-stu-id="f3219-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="f3219-109">[in] The `mdToken` of the base class.</span><span class="sxs-lookup"><span data-stu-id="f3219-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="f3219-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span><span class="sxs-lookup"><span data-stu-id="f3219-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="f3219-111">[in] An array of tokens for the interfaces that this type implements.</span><span class="sxs-lookup"><span data-stu-id="f3219-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="f3219-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f3219-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="f3219-113">The last element of the array is must be `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="f3219-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3219-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3219-114">Requirements</span></span>  
 <span data-ttu-id="f3219-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3219-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3219-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3219-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3219-117">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3219-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3219-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3219-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3219-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3219-119">See also</span></span>

- [<span data-ttu-id="f3219-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f3219-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f3219-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f3219-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
