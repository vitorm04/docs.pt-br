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
ms.openlocfilehash: b72088e4aa9994ca6ae411ec36d4c578e3017e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447877"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="804ba-102">Método IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="804ba-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="804ba-103">Define os recursos de um tipo definido por uma chamada anterior ao [Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="804ba-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="804ba-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="804ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="804ba-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="804ba-106">[in] Um `mdTypeDef` token obtido da chamada original para [Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="804ba-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="804ba-107">[in] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="804ba-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="804ba-108">Esse é um bitmask de `CorTypeAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="804ba-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="804ba-109">[in] O `mdToken` da classe base.</span><span class="sxs-lookup"><span data-stu-id="804ba-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="804ba-110">Obtido de uma chamada anterior a [: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), ou `null`.</span><span class="sxs-lookup"><span data-stu-id="804ba-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="804ba-111">[in] Uma matriz de tokens para as interfaces implementadas por este tipo.</span><span class="sxs-lookup"><span data-stu-id="804ba-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="804ba-112">Essas `mdTypeRef` tokens são obtidos usando [: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="804ba-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="804ba-113">É o último elemento da matriz deve ser `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="804ba-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="804ba-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="804ba-114">Requirements</span></span>  
 <span data-ttu-id="804ba-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="804ba-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="804ba-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="804ba-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="804ba-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="804ba-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="804ba-118">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="804ba-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804ba-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="804ba-119">See Also</span></span>  
 [<span data-ttu-id="804ba-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="804ba-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="804ba-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="804ba-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
