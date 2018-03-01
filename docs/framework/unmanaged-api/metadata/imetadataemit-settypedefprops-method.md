---
title: "Método IMetaDataEmit::SetTypeDefProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a03b781865b55b832b34bfdab7c88ce33f4e9e12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="2493e-102">Método IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="2493e-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="2493e-103">Define os recursos de um tipo definido por uma chamada anterior ao [Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="2493e-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2493e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2493e-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2493e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2493e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="2493e-106">[in] Um `mdTypeDef` token obtido da chamada original para [Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="2493e-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="2493e-107">[in] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="2493e-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="2493e-108">Esse é um bitmask de `CorTypeAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="2493e-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="2493e-109">[in] O `mdToken` da classe base.</span><span class="sxs-lookup"><span data-stu-id="2493e-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="2493e-110">Obtido de uma chamada anterior a [: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), ou `null`.</span><span class="sxs-lookup"><span data-stu-id="2493e-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="2493e-111">[in] Uma matriz de tokens para as interfaces implementadas por este tipo.</span><span class="sxs-lookup"><span data-stu-id="2493e-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="2493e-112">Essas `mdTypeRef` tokens são obtidos usando [: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="2493e-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="2493e-113">É o último elemento da matriz deve ser `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="2493e-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2493e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2493e-114">Requirements</span></span>  
 <span data-ttu-id="2493e-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2493e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2493e-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2493e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2493e-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2493e-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2493e-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2493e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2493e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2493e-119">See Also</span></span>  
 [<span data-ttu-id="2493e-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="2493e-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2493e-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="2493e-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
