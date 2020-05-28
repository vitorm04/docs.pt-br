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
ms.openlocfilehash: 7babd0a90b9882acb03b6360753f55c57a399b9e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005616"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="c575c-102">Método IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="c575c-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="c575c-103">Cria uma definição para um evento com a assinatura de metadados especificada e Obtém um token para essa definição de evento.</span><span class="sxs-lookup"><span data-stu-id="c575c-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c575c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c575c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c575c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c575c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c575c-106">no O token para a classe ou interface de destino.</span><span class="sxs-lookup"><span data-stu-id="c575c-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="c575c-107">Esse é um `mdTypeDef` token ou `mdTypeDefNil` .</span><span class="sxs-lookup"><span data-stu-id="c575c-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="c575c-108">no O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="c575c-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="c575c-109">no Sinalizadores de eventos.</span><span class="sxs-lookup"><span data-stu-id="c575c-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="c575c-110">no O token para a classe de evento.</span><span class="sxs-lookup"><span data-stu-id="c575c-110">[in] The token for the event class.</span></span> <span data-ttu-id="c575c-111">Este é um `mdTypeDef` , um `mdTypeRef` ou um `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="c575c-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="c575c-112">no O método usado para assinar o evento ou nulo.</span><span class="sxs-lookup"><span data-stu-id="c575c-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="c575c-113">no O método usado para cancelar a assinatura do evento, ou NULL.</span><span class="sxs-lookup"><span data-stu-id="c575c-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="c575c-114">no O método usado (por uma classe derivada) para gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="c575c-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="c575c-115">no Uma matriz de tokens para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="c575c-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="c575c-116">A matriz é encerrada com um `mdMethodDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="c575c-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="c575c-117">fora O token de metadados atribuído ao evento.</span><span class="sxs-lookup"><span data-stu-id="c575c-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c575c-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c575c-118">Requirements</span></span>  
 <span data-ttu-id="c575c-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c575c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c575c-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c575c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c575c-121">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c575c-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c575c-122">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c575c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c575c-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="c575c-123">See also</span></span>

- [<span data-ttu-id="c575c-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c575c-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c575c-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c575c-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
