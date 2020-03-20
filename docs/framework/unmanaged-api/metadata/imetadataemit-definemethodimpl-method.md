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
ms.openlocfilehash: 64d76efa8c2f29fda559e5c84217b865540027ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175818"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="70cfb-102">Método IMetaDataEmit::DefineMethodImpl</span><span class="sxs-lookup"><span data-stu-id="70cfb-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="70cfb-103">Cria uma definição para a implementação de um método herdado de uma interface e retorna um token para essa definição de implementação de método.</span><span class="sxs-lookup"><span data-stu-id="70cfb-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cfb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70cfb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70cfb-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="70cfb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="70cfb-106">[em] O `mdTypedef` símbolo da classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="70cfb-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="70cfb-107">[em] O `mdMethodDef` `mdMemberRef` símbolo do corpo de código.</span><span class="sxs-lookup"><span data-stu-id="70cfb-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="70cfb-108">[em] O `mdMethodDef` `mdMemberRef` ou token do método de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="70cfb-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70cfb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70cfb-109">Requirements</span></span>  
 <span data-ttu-id="70cfb-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70cfb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cfb-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70cfb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70cfb-112">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70cfb-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70cfb-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70cfb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cfb-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="70cfb-114">See also</span></span>

- [<span data-ttu-id="70cfb-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="70cfb-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="70cfb-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="70cfb-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
