---
title: Método IMetaDataEmit::SetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177521"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="1af98-102">Método IMetaDataEmit::SetEventProps</span><span class="sxs-lookup"><span data-stu-id="1af98-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="1af98-103">Define ou atualiza o recurso especificado de um evento definido por uma chamada anterior ao [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="1af98-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1af98-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="1af98-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="1af98-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="1af98-106">[em] O token do evento.</span><span class="sxs-lookup"><span data-stu-id="1af98-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="1af98-107">[em] Bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="1af98-107">[in] Event flags.</span></span> <span data-ttu-id="1af98-108">Isto é uma `CorEventAttr` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="1af98-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="1af98-109">[em] O símbolo para a aula de eventos.</span><span class="sxs-lookup"><span data-stu-id="1af98-109">[in] The token for the event class.</span></span> <span data-ttu-id="1af98-110">Isso é `mdTypeDef` um `mdTypeRef` ou um símbolo.</span><span class="sxs-lookup"><span data-stu-id="1af98-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="1af98-111">[em] O método usado para subscrever o evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="1af98-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="1af98-112">[em] O método usado para cancelar a inscrição do evento, ou nulo.</span><span class="sxs-lookup"><span data-stu-id="1af98-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="1af98-113">[em] O método utilizado (por uma classe derivada) para elevar o evento.</span><span class="sxs-lookup"><span data-stu-id="1af98-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="1af98-114">[em] Uma matriz de tokens para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="1af98-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="1af98-115">O último elemento da `mdMethodDefNil`matriz deve ser .</span><span class="sxs-lookup"><span data-stu-id="1af98-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1af98-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1af98-116">Requirements</span></span>  
 <span data-ttu-id="1af98-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1af98-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1af98-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1af98-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1af98-119">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1af98-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1af98-120">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1af98-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af98-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="1af98-121">See also</span></span>

- [<span data-ttu-id="1af98-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1af98-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1af98-123">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1af98-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
