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
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008749"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="b490f-102">Método IMetaDataEmit::SetEventProps</span><span class="sxs-lookup"><span data-stu-id="b490f-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="b490f-103">Define ou atualiza o recurso especificado de um evento definido por uma chamada anterior para [IMetaDataEmit::D efineevent](imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="b490f-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b490f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b490f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b490f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b490f-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="b490f-106">no O token do evento.</span><span class="sxs-lookup"><span data-stu-id="b490f-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="b490f-107">no Sinalizadores de eventos.</span><span class="sxs-lookup"><span data-stu-id="b490f-107">[in] Event flags.</span></span> <span data-ttu-id="b490f-108">Esta é uma bitmask de `CorEventAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="b490f-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="b490f-109">no O token para a classe de evento.</span><span class="sxs-lookup"><span data-stu-id="b490f-109">[in] The token for the event class.</span></span> <span data-ttu-id="b490f-110">Este é um `mdTypeDef` `mdTypeRef` token ou.</span><span class="sxs-lookup"><span data-stu-id="b490f-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="b490f-111">no O método usado para assinar o evento ou nulo.</span><span class="sxs-lookup"><span data-stu-id="b490f-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="b490f-112">no O método usado para cancelar a assinatura do evento, ou NULL.</span><span class="sxs-lookup"><span data-stu-id="b490f-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="b490f-113">no O método usado (por uma classe derivada) para gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="b490f-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="b490f-114">no Uma matriz de tokens para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="b490f-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="b490f-115">O último elemento da matriz deve ser `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="b490f-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b490f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b490f-116">Requirements</span></span>  
 <span data-ttu-id="b490f-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b490f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b490f-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b490f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b490f-119">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b490f-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b490f-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b490f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b490f-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="b490f-121">See also</span></span>

- [<span data-ttu-id="b490f-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b490f-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b490f-123">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b490f-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
