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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596888a8eb4a55c4cfe594b1911f17f6d32f56d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992427"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="11771-102">Método IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="11771-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="11771-103">Define os recursos de um tipo definido por uma chamada anterior a [imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="11771-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11771-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11771-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11771-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11771-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="11771-106">[in] Uma `mdTypeDef` token obtido do chamada original à [imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="11771-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="11771-107">[in] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="11771-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="11771-108">Esse é um bitmask de `CorTypeAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="11771-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="11771-109">[in] O `mdToken` da classe base.</span><span class="sxs-lookup"><span data-stu-id="11771-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="11771-110">Obtido de uma chamada anterior a [imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), ou `null`.</span><span class="sxs-lookup"><span data-stu-id="11771-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="11771-111">[in] Uma matriz de tokens para as interfaces que esse tipo implementa.</span><span class="sxs-lookup"><span data-stu-id="11771-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="11771-112">Eles `mdTypeRef` tokens são obtidos usando [imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="11771-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="11771-113">É o último elemento da matriz deve ser `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="11771-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11771-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11771-114">Requirements</span></span>  
 <span data-ttu-id="11771-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11771-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11771-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11771-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11771-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="11771-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11771-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11771-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11771-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11771-119">See also</span></span>

- [<span data-ttu-id="11771-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="11771-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="11771-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="11771-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
