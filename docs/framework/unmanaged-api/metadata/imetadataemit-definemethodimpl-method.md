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
ms.openlocfilehash: b64275def01d7b62f9a461de69a286769094305e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777591"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="2e7dc-102">Método IMetaDataEmit::DefineMethodImpl</span><span class="sxs-lookup"><span data-stu-id="2e7dc-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="2e7dc-103">Cria uma definição para a implementação de um método herdado de uma interface e retorna um token para essa definição de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e7dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e7dc-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e7dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e7dc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="2e7dc-106">[in] O `mdTypedef` token da classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="2e7dc-107">[in] O `mdMethodDef` ou `mdMemberRef` token do corpo do código.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="2e7dc-108">[in] O `mdMethodDef` ou `mdMemberRef` token do método de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e7dc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e7dc-109">Requirements</span></span>  
 <span data-ttu-id="2e7dc-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e7dc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e7dc-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e7dc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e7dc-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2e7dc-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e7dc-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e7dc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7dc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e7dc-114">See also</span></span>

- [<span data-ttu-id="2e7dc-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="2e7dc-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2e7dc-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="2e7dc-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
