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
ms.openlocfilehash: 7389e9233fd946cdb2c810bec01cfbfffc8b707d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175597"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="9d384-102">Método IMetaDataEmit::SetParent</span><span class="sxs-lookup"><span data-stu-id="9d384-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="9d384-103">Estabelece que o membro especificado, conforme definido por uma chamada anterior ao [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), é um membro do tipo especificado, conforme definido por uma chamada anterior ao [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="9d384-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d384-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d384-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d384-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d384-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="9d384-106">[em] O `mdMemberRef` símbolo para receber um novo pai.</span><span class="sxs-lookup"><span data-stu-id="9d384-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="9d384-107">[em] O `mdToken` para o novo pai.</span><span class="sxs-lookup"><span data-stu-id="9d384-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d384-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d384-108">Requirements</span></span>  
 <span data-ttu-id="9d384-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d384-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d384-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d384-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d384-111">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d384-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d384-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d384-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d384-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d384-113">See also</span></span>

- [<span data-ttu-id="9d384-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9d384-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9d384-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9d384-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
