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
ms.openlocfilehash: 126cf950b71ed2325006b14927ae95517f7c6dc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="7aec7-102">Método IMetaDataEmit::DefineMethodImpl</span><span class="sxs-lookup"><span data-stu-id="7aec7-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="7aec7-103">Cria uma definição para a implementação de um método herdado de uma interface e retorna um token para que a definição de implementação de método.</span><span class="sxs-lookup"><span data-stu-id="7aec7-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aec7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7aec7-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7aec7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7aec7-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7aec7-106">[in] O `mdTypedef` token de classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="7aec7-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="7aec7-107">[in] O `mdMethodDef` ou `mdMethodRef` token do corpo do código.</span><span class="sxs-lookup"><span data-stu-id="7aec7-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="7aec7-108">[in] O `mdMethodDef` ou `mdMethodRef` token do método de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="7aec7-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aec7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7aec7-109">Requirements</span></span>  
 <span data-ttu-id="7aec7-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aec7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aec7-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7aec7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7aec7-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7aec7-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7aec7-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aec7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aec7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7aec7-114">See Also</span></span>  
 [<span data-ttu-id="7aec7-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7aec7-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7aec7-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7aec7-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
