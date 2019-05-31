---
title: Método IMetaDataEmit::DefineMethodImpl
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 184ae0aee6947aa686e80541ab3ba36e0f4e1647
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424009"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="76500-102">Método IMetaDataEmit::DefineMethodImpl</span><span class="sxs-lookup"><span data-stu-id="76500-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="76500-103">Cria uma definição para a implementação de um método herdado de uma interface e retorna um token para essa definição de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="76500-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76500-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76500-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76500-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76500-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="76500-106">[in] O `mdTypedef` token da classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="76500-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="76500-107">[in] O `mdMethodDef` ou `mdMemberRef` token do corpo do código.</span><span class="sxs-lookup"><span data-stu-id="76500-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="76500-108">[in] O `mdMethodDef` ou `mdMemberRef` token do método de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="76500-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76500-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76500-109">Requirements</span></span>  
 <span data-ttu-id="76500-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76500-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76500-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76500-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76500-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="76500-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76500-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76500-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76500-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76500-114">See also</span></span>

- [<span data-ttu-id="76500-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="76500-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="76500-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="76500-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
