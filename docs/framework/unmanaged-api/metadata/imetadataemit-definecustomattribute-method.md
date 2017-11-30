---
title: "Método IMetaDataEmit::DefineCustomAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineCustomAttribute
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c4c00480571b4160d7442aeafea088fe8d04ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="6e4dc-102">Método IMetaDataEmit::DefineCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="6e4dc-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="6e4dc-103">Cria uma definição de um atributo personalizado com a assinatura de metadados especificado, a ser anexado ao objeto especificado e recebe um token para essa definição de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e4dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e4dc-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e4dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e4dc-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="6e4dc-106">[in] O token para o item de proprietário.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="6e4dc-107">[in] O token que identifica o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="6e4dc-108">[in] Um ponteiro para o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="6e4dc-109">[in] A contagem de bytes em `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="6e4dc-110">[out] O `mdCustomAttribute` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e4dc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e4dc-111">Requirements</span></span>  
 <span data-ttu-id="6e4dc-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e4dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e4dc-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e4dc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e4dc-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6e4dc-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e4dc-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e4dc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4dc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e4dc-116">See Also</span></span>  
 [<span data-ttu-id="6e4dc-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="6e4dc-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6e4dc-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="6e4dc-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
