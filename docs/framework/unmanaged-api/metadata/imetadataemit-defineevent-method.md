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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175844"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="31e7e-102">Método IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="31e7e-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="31e7e-103">Cria uma definição para um evento com a assinatura de metadados especificada e obtém um token para essa definição de evento.</span><span class="sxs-lookup"><span data-stu-id="31e7e-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31e7e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="31e7e-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="31e7e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="31e7e-106">[em] O token para a classe de destino ou interface.</span><span class="sxs-lookup"><span data-stu-id="31e7e-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="31e7e-107">Isso é `mdTypeDef` um `mdTypeDefNil` símbolo.</span><span class="sxs-lookup"><span data-stu-id="31e7e-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="31e7e-108">[em] O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="31e7e-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="31e7e-109">[em] Bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="31e7e-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="31e7e-110">[em] O símbolo para a aula de eventos.</span><span class="sxs-lookup"><span data-stu-id="31e7e-110">[in] The token for the event class.</span></span> <span data-ttu-id="31e7e-111">Isto `mdTypeDef`é `mdTypeRef`um, `mdTokenNil` a, ou um símbolo.</span><span class="sxs-lookup"><span data-stu-id="31e7e-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="31e7e-112">[em] O método usado para subscrever o evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="31e7e-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="31e7e-113">[em] O método usado para cancelar a inscrição do evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="31e7e-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="31e7e-114">[em] O método utilizado (por uma classe derivada) para elevar o evento.</span><span class="sxs-lookup"><span data-stu-id="31e7e-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="31e7e-115">[em] Uma matriz de tokens para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="31e7e-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="31e7e-116">A matriz é encerrada `mdMethodDefNil` com um token.</span><span class="sxs-lookup"><span data-stu-id="31e7e-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="31e7e-117">[fora] O token de metadados atribuído ao evento.</span><span class="sxs-lookup"><span data-stu-id="31e7e-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e7e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31e7e-118">Requirements</span></span>  
 <span data-ttu-id="31e7e-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31e7e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e7e-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31e7e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31e7e-121">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31e7e-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31e7e-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e7e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e7e-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="31e7e-123">See also</span></span>

- [<span data-ttu-id="31e7e-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="31e7e-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="31e7e-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="31e7e-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
