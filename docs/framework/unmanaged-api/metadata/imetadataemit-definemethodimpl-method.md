---
title: "Método IMetaDataEmit::DefineMethodImpl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5bf16c51a241a01f18aae84f8b3bb7554f08b87c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="45897-102">Método IMetaDataEmit::DefineMethodImpl</span><span class="sxs-lookup"><span data-stu-id="45897-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="45897-103">Cria uma definição para a implementação de um método herdado de uma interface e retorna um token para que a definição de implementação de método.</span><span class="sxs-lookup"><span data-stu-id="45897-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45897-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45897-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45897-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45897-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="45897-106">[in] O `mdTypedef` token de classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="45897-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="45897-107">[in] O `mdMethodDef` ou `mdMethodRef` token do corpo do código.</span><span class="sxs-lookup"><span data-stu-id="45897-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="45897-108">[in] O `mdMethodDef` ou `mdMethodRef` token do método de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="45897-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45897-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45897-109">Requirements</span></span>  
 <span data-ttu-id="45897-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45897-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45897-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="45897-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45897-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="45897-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45897-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45897-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45897-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45897-114">See Also</span></span>  
 [<span data-ttu-id="45897-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="45897-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="45897-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="45897-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
