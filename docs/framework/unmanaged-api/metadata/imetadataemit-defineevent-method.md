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
ms.openlocfilehash: ce94765467899ac7c906b0dfcdf0ceb78c659b5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448198"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="df5c3-102">Método IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="df5c3-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="df5c3-103">Cria uma definição para um evento com a assinatura de metadados especificado e obtém um token a definição desse evento.</span><span class="sxs-lookup"><span data-stu-id="df5c3-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df5c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df5c3-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="df5c3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df5c3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="df5c3-106">[in] O token para a interface ou classe de destino.</span><span class="sxs-lookup"><span data-stu-id="df5c3-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="df5c3-107">Isso é uma `mdTypeDef` ou `mdTypeDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="df5c3-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="df5c3-108">[in] O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="df5c3-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="df5c3-109">[in] Sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="df5c3-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="df5c3-110">[in] O token para a classe de evento.</span><span class="sxs-lookup"><span data-stu-id="df5c3-110">[in] The token for the event class.</span></span> <span data-ttu-id="df5c3-111">Este é um `mdTypeDef`, um `mdTypeRef`, ou um `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="df5c3-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="df5c3-112">[in] O método usado para assinar o evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="df5c3-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="df5c3-113">[in] O método usado para cancelar a assinatura do evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="df5c3-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="df5c3-114">[in] O método usado (por uma classe derivada) para gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="df5c3-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="df5c3-115">[in] Uma matriz de tokens de outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="df5c3-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="df5c3-116">A matriz é encerrada com um `mdMethodDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="df5c3-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="df5c3-117">[out] O token de metadados atribuído ao evento.</span><span class="sxs-lookup"><span data-stu-id="df5c3-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df5c3-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df5c3-118">Requirements</span></span>  
 <span data-ttu-id="df5c3-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df5c3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df5c3-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df5c3-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df5c3-121">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="df5c3-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df5c3-122">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df5c3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df5c3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df5c3-123">See Also</span></span>  
 [<span data-ttu-id="df5c3-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="df5c3-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="df5c3-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="df5c3-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
