---
title: "Método IMetaDataEmit::SetEventProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167e56052550fa844d1265802455b3cbf6368ba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="69c8f-102">Método IMetaDataEmit::SetEventProps</span><span class="sxs-lookup"><span data-stu-id="69c8f-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="69c8f-103">Define ou atualiza o recurso especificado de um evento definido por uma chamada anterior ao [: Defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="69c8f-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c8f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69c8f-104">Syntax</span></span>  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69c8f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c8f-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="69c8f-106">[in] O token de evento.</span><span class="sxs-lookup"><span data-stu-id="69c8f-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="69c8f-107">[in] Sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="69c8f-107">[in] Event flags.</span></span> <span data-ttu-id="69c8f-108">Esse é um bitmask de `CorEventAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="69c8f-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="69c8f-109">[in] O token para a classe de evento.</span><span class="sxs-lookup"><span data-stu-id="69c8f-109">[in] The token for the event class.</span></span> <span data-ttu-id="69c8f-110">Isso é uma `mdTypeDef` ou um `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="69c8f-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="69c8f-111">[in] O método usado para assinar o evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="69c8f-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="69c8f-112">[in] O método usado para cancelar a assinatura do evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="69c8f-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="69c8f-113">[in] O método usado (por uma classe derivada) para gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="69c8f-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="69c8f-114">[in] Uma matriz de tokens de outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="69c8f-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="69c8f-115">O último elemento da matriz deve ser `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="69c8f-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c8f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69c8f-116">Requirements</span></span>  
 <span data-ttu-id="69c8f-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69c8f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69c8f-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="69c8f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69c8f-119">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="69c8f-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69c8f-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69c8f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c8f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69c8f-121">See Also</span></span>  
 [<span data-ttu-id="69c8f-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="69c8f-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="69c8f-123">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="69c8f-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
