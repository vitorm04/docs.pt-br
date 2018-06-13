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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00a28e0f7ab03af8d5f2fc0dda5274f9aaa4dca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449089"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="df22f-102">Método IMetaDataImport::EnumMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="df22f-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="df22f-103">Enumera as propriedades e os eventos de alteração de propriedade ao qual o método especificado está relacionado.</span><span class="sxs-lookup"><span data-stu-id="df22f-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df22f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df22f-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df22f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df22f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="df22f-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="df22f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="df22f-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="df22f-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="df22f-108">[in] Um token MethodDef que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="df22f-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="df22f-109">[out] A matriz usada para armazenar os eventos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="df22f-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="df22f-110">[in] O tamanho máximo da `rEventProp` matriz.</span><span class="sxs-lookup"><span data-stu-id="df22f-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="df22f-111">[out] O número de eventos ou propriedades retornadas em `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="df22f-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df22f-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="df22f-112">Return Value</span></span>  
  
|<span data-ttu-id="df22f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df22f-113">HRESULT</span></span>|<span data-ttu-id="df22f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="df22f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="df22f-115">`EnumMethodSemantics` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="df22f-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="df22f-116">Não existem eventos ou propriedades para enumerar.</span><span class="sxs-lookup"><span data-stu-id="df22f-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="df22f-117">Nesse caso, `pcEventProp` é zero.</span><span class="sxs-lookup"><span data-stu-id="df22f-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df22f-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="df22f-118">Remarks</span></span>  
 <span data-ttu-id="df22f-119">Definem muitos tipos common language runtime *propriedade* `Changed` eventos e `On` *propriedade* `Changed` métodos relacionados às suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="df22f-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="df22f-120">Por exemplo, o <xref:System.Windows.Forms.Control?displayProperty=nameWithType> tipo define uma <xref:System.Windows.Forms.Control.Font%2A> propriedade, um <xref:System.Windows.Forms.Control.FontChanged> evento e um <xref:System.Windows.Forms.Control.OnFontChanged%2A> método.</span><span class="sxs-lookup"><span data-stu-id="df22f-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="df22f-121">O método de acessador de conjunto do <xref:System.Windows.Forms.Control.Font%2A> chamadas de propriedade <xref:System.Windows.Forms.Control.OnFontChanged%2A> método, que por sua vez gera o <xref:System.Windows.Forms.Control.FontChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="df22f-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="df22f-122">Você poderia chamar `EnumMethodSemantics` usando MethodDef para <xref:System.Windows.Forms.Control.OnFontChanged%2A> obter referências para o <xref:System.Windows.Forms.Control.Font%2A> propriedade e o <xref:System.Windows.Forms.Control.FontChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="df22f-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df22f-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df22f-123">Requirements</span></span>  
 <span data-ttu-id="df22f-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df22f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df22f-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df22f-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df22f-126">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="df22f-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df22f-127">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df22f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df22f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df22f-128">See Also</span></span>  
 [<span data-ttu-id="df22f-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="df22f-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="df22f-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="df22f-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
