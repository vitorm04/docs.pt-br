---
title: Método IMetaDataEmit::SetParent
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: d821413e67b36392d936499cd22f2e065f1556ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503842"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="a6456-102">Método IMetaDataEmit::SetParent</span><span class="sxs-lookup"><span data-stu-id="a6456-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="a6456-103">Estabelece que o membro especificado, conforme definido por uma chamada anterior a [IMetaDataEmit::D efinememberref](imetadataemit-definememberref-method.md), é um membro do tipo especificado, conforme definido por uma chamada anterior para [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="a6456-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6456-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6456-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6456-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6456-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="a6456-106">no O `mdMemberRef` token para receber um novo pai.</span><span class="sxs-lookup"><span data-stu-id="a6456-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="a6456-107">no O `mdToken` para o novo pai.</span><span class="sxs-lookup"><span data-stu-id="a6456-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6456-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6456-108">Requirements</span></span>  
 <span data-ttu-id="a6456-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6456-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6456-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a6456-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6456-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a6456-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6456-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6456-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6456-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="a6456-113">See also</span></span>

- [<span data-ttu-id="a6456-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a6456-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a6456-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a6456-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
