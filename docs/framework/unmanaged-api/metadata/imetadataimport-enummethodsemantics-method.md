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
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175454"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="e53da-102">Método IMetaDataImport::EnumMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="e53da-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="e53da-103">Enumera as propriedades e os eventos de alteração de propriedade aos quais o método especificado está relacionado.</span><span class="sxs-lookup"><span data-stu-id="e53da-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e53da-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e53da-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e53da-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e53da-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="e53da-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e53da-107">Isto deve ser NULO para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="e53da-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="e53da-108">[em] Um token MethodDef que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="e53da-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="e53da-109">[fora] A matriz usada para armazenar os eventos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="e53da-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e53da-110">[em] O tamanho máximo `rEventProp` da matriz.</span><span class="sxs-lookup"><span data-stu-id="e53da-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="e53da-111">[fora] O número de eventos ou `rEventProp`propriedades retornadas em .</span><span class="sxs-lookup"><span data-stu-id="e53da-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e53da-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e53da-112">Return Value</span></span>  
  
|<span data-ttu-id="e53da-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e53da-113">HRESULT</span></span>|<span data-ttu-id="e53da-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e53da-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e53da-115">`EnumMethodSemantics`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="e53da-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e53da-116">Não há eventos ou propriedades para enumerar.</span><span class="sxs-lookup"><span data-stu-id="e53da-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="e53da-117">Nesse caso, `pcEventProp` é zero.</span><span class="sxs-lookup"><span data-stu-id="e53da-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e53da-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="e53da-118">Remarks</span></span>  
 <span data-ttu-id="e53da-119">Muitos tipos de tempo de `On`execução de idiomas comuns definem eventos de *propriedade* `Changed` e métodos de *propriedade* `Changed` relacionados às suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="e53da-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="e53da-120">Por exemplo, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> o tipo <xref:System.Windows.Forms.Control.Font%2A> define <xref:System.Windows.Forms.Control.FontChanged> uma propriedade, <xref:System.Windows.Forms.Control.OnFontChanged%2A> um evento e um método.</span><span class="sxs-lookup"><span data-stu-id="e53da-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="e53da-121">O método de <xref:System.Windows.Forms.Control.Font%2A> acessório <xref:System.Windows.Forms.Control.OnFontChanged%2A> definido do método de <xref:System.Windows.Forms.Control.FontChanged> chamadas de propriedade, que por sua vez levanta o evento.</span><span class="sxs-lookup"><span data-stu-id="e53da-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="e53da-122">Você `EnumMethodSemantics` ligaria usando o <xref:System.Windows.Forms.Control.OnFontChanged%2A> MethodDef para <xref:System.Windows.Forms.Control.Font%2A> obter referências à propriedade e ao <xref:System.Windows.Forms.Control.FontChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="e53da-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e53da-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e53da-123">Requirements</span></span>  
 <span data-ttu-id="e53da-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e53da-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e53da-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e53da-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e53da-126">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e53da-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e53da-127">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e53da-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53da-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="e53da-128">See also</span></span>

- [<span data-ttu-id="e53da-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e53da-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e53da-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e53da-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
