---
title: Método IMetaDataImport::EnumMethodSemantics
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: 213cbd955e3d47a49abde579a54af48641e225ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491908"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="a10f2-102">Método IMetaDataImport::EnumMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="a10f2-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="a10f2-103">Enumera as propriedades e os eventos de alteração de propriedade aos quais o método especificado está relacionado.</span><span class="sxs-lookup"><span data-stu-id="a10f2-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a10f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a10f2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a10f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a10f2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a10f2-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="a10f2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a10f2-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="a10f2-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="a10f2-108">no Um token MethodDef que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="a10f2-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="a10f2-109">fora A matriz usada para armazenar os eventos ou as propriedades.</span><span class="sxs-lookup"><span data-stu-id="a10f2-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a10f2-110">no O tamanho máximo da `rEventProp` matriz.</span><span class="sxs-lookup"><span data-stu-id="a10f2-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="a10f2-111">fora O número de eventos ou Propriedades retornados em `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="a10f2-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a10f2-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="a10f2-112">Return Value</span></span>  
  
|<span data-ttu-id="a10f2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a10f2-113">HRESULT</span></span>|<span data-ttu-id="a10f2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a10f2-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a10f2-115">`EnumMethodSemantics`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a10f2-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a10f2-116">Não há eventos ou propriedades para enumerar.</span><span class="sxs-lookup"><span data-stu-id="a10f2-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="a10f2-117">Nesse caso, `pcEventProp` é zero.</span><span class="sxs-lookup"><span data-stu-id="a10f2-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a10f2-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a10f2-118">Remarks</span></span>  
 <span data-ttu-id="a10f2-119">Muitos tipos de Common Language Runtime definem eventos de *Propriedade* `Changed` e `On` *Property* `Changed` métodos de propriedade relacionados a suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="a10f2-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="a10f2-120">Por exemplo, o <xref:System.Windows.Forms.Control?displayProperty=nameWithType> tipo define uma <xref:System.Windows.Forms.Control.Font%2A> propriedade, um <xref:System.Windows.Forms.Control.FontChanged> evento e um <xref:System.Windows.Forms.Control.OnFontChanged%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a10f2-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="a10f2-121">O método do acessador set do <xref:System.Windows.Forms.Control.Font%2A> método de chamadas de propriedade <xref:System.Windows.Forms.Control.OnFontChanged%2A> que, por sua vez, gera o <xref:System.Windows.Forms.Control.FontChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="a10f2-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="a10f2-122">Você chamaria `EnumMethodSemantics` usando o MethodDef para <xref:System.Windows.Forms.Control.OnFontChanged%2A> para obter referências à <xref:System.Windows.Forms.Control.Font%2A> propriedade e ao <xref:System.Windows.Forms.Control.FontChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="a10f2-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a10f2-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a10f2-123">Requirements</span></span>  
 <span data-ttu-id="a10f2-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a10f2-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a10f2-125">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a10f2-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a10f2-126">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a10f2-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a10f2-127">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a10f2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10f2-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="a10f2-128">See also</span></span>

- [<span data-ttu-id="a10f2-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a10f2-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a10f2-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a10f2-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
