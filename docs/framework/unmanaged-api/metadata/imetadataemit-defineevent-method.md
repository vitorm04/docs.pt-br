---
title: Método IMetaDataEmit::DefineEvent
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7d42fe17af5b10d718d0e2b6a7ae33644fa4813
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730289"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="7b67d-102">Método IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="7b67d-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="7b67d-103">Cria uma definição para um evento com a assinatura de metadados especificado e obtém um token a definição desse evento.</span><span class="sxs-lookup"><span data-stu-id="7b67d-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b67d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b67d-104">Syntax</span></span>  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b67d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b67d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7b67d-106">[in] O token para a interface ou classe de destino.</span><span class="sxs-lookup"><span data-stu-id="7b67d-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="7b67d-107">Isso é um `mdTypeDef` ou `mdTypeDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="7b67d-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="7b67d-108">[in] O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="7b67d-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="7b67d-109">[in] Sinalizadores de eventos.</span><span class="sxs-lookup"><span data-stu-id="7b67d-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="7b67d-110">[in] O token para a classe de evento.</span><span class="sxs-lookup"><span data-stu-id="7b67d-110">[in] The token for the event class.</span></span> <span data-ttu-id="7b67d-111">Esse é um `mdTypeDef`, um `mdTypeRef`, ou um `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="7b67d-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="7b67d-112">[in] O método usado para assinar o evento, ou null.</span><span class="sxs-lookup"><span data-stu-id="7b67d-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="7b67d-113">[in] O método usado para cancelar a assinatura para o evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="7b67d-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="7b67d-114">[in] O método usado (por uma classe derivada) para gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="7b67d-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="7b67d-115">[in] Uma matriz de tokens para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="7b67d-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="7b67d-116">A matriz é encerrada com um `mdMethodDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="7b67d-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="7b67d-117">[out] O token de metadados atribuído ao evento.</span><span class="sxs-lookup"><span data-stu-id="7b67d-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b67d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b67d-118">Requirements</span></span>  
 <span data-ttu-id="7b67d-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b67d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b67d-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7b67d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b67d-121">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7b67d-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b67d-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b67d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b67d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b67d-123">See also</span></span>
- [<span data-ttu-id="7b67d-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7b67d-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7b67d-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7b67d-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
