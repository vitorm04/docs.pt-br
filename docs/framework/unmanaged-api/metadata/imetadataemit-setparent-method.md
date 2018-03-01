---
title: "Método IMetaDataEmit::SetParent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ede8541cbf0f5d66c4d6c4ecf3bd7fee8e296038
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="9eaec-102">Método IMetaDataEmit::SetParent</span><span class="sxs-lookup"><span data-stu-id="9eaec-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="9eaec-103">Estabelece que o membro especificado, conforme definido por uma chamada anterior ao [: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), é um membro do tipo especificado, conforme definido por uma chamada anterior ao [Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="9eaec-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eaec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9eaec-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9eaec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9eaec-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="9eaec-106">[in] O `mdMemberRef` token para receber um novo pai.</span><span class="sxs-lookup"><span data-stu-id="9eaec-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="9eaec-107">[in] O `mdToken` para o novo pai.</span><span class="sxs-lookup"><span data-stu-id="9eaec-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eaec-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9eaec-108">Requirements</span></span>  
 <span data-ttu-id="9eaec-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eaec-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eaec-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9eaec-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9eaec-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9eaec-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9eaec-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eaec-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eaec-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eaec-113">See Also</span></span>  
 [<span data-ttu-id="9eaec-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9eaec-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9eaec-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9eaec-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
