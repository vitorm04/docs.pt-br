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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe27d8a0508a13c1f54eef00d5119bec4daec4a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140433"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="720e8-102">Método IMetaDataEmit::SetParent</span><span class="sxs-lookup"><span data-stu-id="720e8-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="720e8-103">Estabelece que o membro especificado, conforme definido por uma chamada anterior a [imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), é um membro do tipo especificado, conforme definido por uma chamada anterior a [imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="720e8-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="720e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="720e8-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="720e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="720e8-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="720e8-106">[in] O `mdMemberRef` token para receber um novo pai.</span><span class="sxs-lookup"><span data-stu-id="720e8-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="720e8-107">[in] O `mdToken` para o novo pai.</span><span class="sxs-lookup"><span data-stu-id="720e8-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="720e8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="720e8-108">Requirements</span></span>  
 <span data-ttu-id="720e8-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="720e8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="720e8-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="720e8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="720e8-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="720e8-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="720e8-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="720e8-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="720e8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="720e8-113">See also</span></span>

- [<span data-ttu-id="720e8-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="720e8-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="720e8-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="720e8-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
