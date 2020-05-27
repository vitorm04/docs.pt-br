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
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007761"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="4db11-102">Método IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="4db11-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="4db11-103">Define recursos de um tipo definido por uma chamada anterior para [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="4db11-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4db11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4db11-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4db11-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4db11-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4db11-106">no Um `mdTypeDef` token obtido da chamada original para [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="4db11-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="4db11-107">[in] `TypeDef` atributos.</span><span class="sxs-lookup"><span data-stu-id="4db11-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="4db11-108">Esta é uma bitmask de `CorTypeAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="4db11-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="4db11-109">no O `mdToken` da classe base.</span><span class="sxs-lookup"><span data-stu-id="4db11-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="4db11-110">Obtido de uma chamada anterior para [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md)ou `null` .</span><span class="sxs-lookup"><span data-stu-id="4db11-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="4db11-111">no Uma matriz de tokens para as interfaces que esse tipo implementa.</span><span class="sxs-lookup"><span data-stu-id="4db11-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="4db11-112">Esses `mdTypeRef` tokens são obtidos usando [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="4db11-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="4db11-113">O último elemento da matriz deve ser `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="4db11-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4db11-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4db11-114">Requirements</span></span>  
 <span data-ttu-id="4db11-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4db11-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4db11-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4db11-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4db11-117">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4db11-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4db11-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4db11-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db11-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="4db11-119">See also</span></span>

- [<span data-ttu-id="4db11-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4db11-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4db11-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4db11-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
