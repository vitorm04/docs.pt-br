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
ms.openlocfilehash: 5ed5afbbf49b6680d00e78b6af3d45c6f0a7229d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004485"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="31c9c-102">Método IMetaDataEmit::DefineMethodImpl</span><span class="sxs-lookup"><span data-stu-id="31c9c-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="31c9c-103">Cria uma definição para implementação de um método herdado de uma interface e retorna um token para essa definição de implementação de método.</span><span class="sxs-lookup"><span data-stu-id="31c9c-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31c9c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31c9c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31c9c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="31c9c-106">no O `mdTypedef` token da classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="31c9c-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="31c9c-107">no O `mdMethodDef` `mdMemberRef` token ou do corpo do código.</span><span class="sxs-lookup"><span data-stu-id="31c9c-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="31c9c-108">no O `mdMethodDef` `mdMemberRef` token ou do método de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="31c9c-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31c9c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31c9c-109">Requirements</span></span>  
 <span data-ttu-id="31c9c-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31c9c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31c9c-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="31c9c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31c9c-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31c9c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31c9c-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31c9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c9c-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="31c9c-114">See also</span></span>

- [<span data-ttu-id="31c9c-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="31c9c-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="31c9c-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="31c9c-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
