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
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450325"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="89090-102">Método IMetaDataEmit::SetEventProps</span><span class="sxs-lookup"><span data-stu-id="89090-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="89090-103">Define ou atualiza o recurso especificado de um evento definido por uma chamada anterior para [IMetaDataEmit::D efineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="89090-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89090-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89090-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="89090-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89090-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="89090-106">no O token do evento.</span><span class="sxs-lookup"><span data-stu-id="89090-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="89090-107">no Sinalizadores de eventos.</span><span class="sxs-lookup"><span data-stu-id="89090-107">[in] Event flags.</span></span> <span data-ttu-id="89090-108">Este é um bitmask de valores de `CorEventAttr`.</span><span class="sxs-lookup"><span data-stu-id="89090-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="89090-109">no O token para a classe de evento.</span><span class="sxs-lookup"><span data-stu-id="89090-109">[in] The token for the event class.</span></span> <span data-ttu-id="89090-110">Este é um `mdTypeDef` ou um token de `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="89090-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="89090-111">no O método usado para assinar o evento ou nulo.</span><span class="sxs-lookup"><span data-stu-id="89090-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="89090-112">no O método usado para cancelar a assinatura do evento, ou NULL.</span><span class="sxs-lookup"><span data-stu-id="89090-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="89090-113">no O método usado (por uma classe derivada) para gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="89090-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="89090-114">no Uma matriz de tokens para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="89090-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="89090-115">O último elemento da matriz deve ser `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="89090-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89090-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="89090-116">Requirements</span></span>  
 <span data-ttu-id="89090-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89090-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89090-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89090-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89090-119">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89090-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89090-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89090-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89090-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89090-121">See also</span></span>

- [<span data-ttu-id="89090-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="89090-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="89090-123">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="89090-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
