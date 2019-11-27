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
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432560"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="26464-102">Método IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="26464-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="26464-103">Cria uma definição para um evento com a assinatura de metadados especificada e Obtém um token para essa definição de evento.</span><span class="sxs-lookup"><span data-stu-id="26464-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26464-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26464-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="26464-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26464-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="26464-106">no O token para a classe ou interface de destino.</span><span class="sxs-lookup"><span data-stu-id="26464-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="26464-107">É um token `mdTypeDef` ou `mdTypeDefNil`.</span><span class="sxs-lookup"><span data-stu-id="26464-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="26464-108">no O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="26464-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="26464-109">no Sinalizadores de eventos.</span><span class="sxs-lookup"><span data-stu-id="26464-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="26464-110">no O token para a classe de evento.</span><span class="sxs-lookup"><span data-stu-id="26464-110">[in] The token for the event class.</span></span> <span data-ttu-id="26464-111">Este é um `mdTypeDef`, um `mdTypeRef`ou um token `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="26464-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="26464-112">no O método usado para assinar o evento ou nulo.</span><span class="sxs-lookup"><span data-stu-id="26464-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="26464-113">no O método usado para cancelar a assinatura do evento, ou NULL.</span><span class="sxs-lookup"><span data-stu-id="26464-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="26464-114">no O método usado (por uma classe derivada) para gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="26464-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="26464-115">no Uma matriz de tokens para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="26464-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="26464-116">A matriz é encerrada com um token `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="26464-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="26464-117">fora O token de metadados atribuído ao evento.</span><span class="sxs-lookup"><span data-stu-id="26464-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26464-118">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="26464-118">Requirements</span></span>  
 <span data-ttu-id="26464-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26464-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26464-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="26464-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26464-121">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26464-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26464-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26464-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26464-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26464-123">See also</span></span>

- [<span data-ttu-id="26464-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="26464-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="26464-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="26464-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
