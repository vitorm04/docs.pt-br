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
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177456"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="80959-102">Método IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="80959-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="80959-103">Define recursos de um tipo definido por uma chamada anterior ao [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="80959-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80959-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80959-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80959-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="80959-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="80959-106">[em] Um `mdTypeDef` token obtido da chamada original para [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="80959-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="80959-107">[em] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="80959-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="80959-108">Isto é uma `CorTypeAttr` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="80959-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="80959-109">[em] A `mdToken` da classe base.</span><span class="sxs-lookup"><span data-stu-id="80959-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="80959-110">Obtido a partir de uma chamada anterior para [IMetaDataEmit::DefineImportType,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)ou `null`.</span><span class="sxs-lookup"><span data-stu-id="80959-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="80959-111">[em] Uma matriz de tokens para as interfaces que esse tipo implementa.</span><span class="sxs-lookup"><span data-stu-id="80959-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="80959-112">Esses `mdTypeRef` tokens são obtidos usando [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="80959-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="80959-113">O último elemento da matriz `mdTokenNil`deve ser .</span><span class="sxs-lookup"><span data-stu-id="80959-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80959-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80959-114">Requirements</span></span>  
 <span data-ttu-id="80959-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80959-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80959-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80959-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80959-117">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80959-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80959-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80959-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80959-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="80959-119">See also</span></span>

- [<span data-ttu-id="80959-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="80959-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="80959-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="80959-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
