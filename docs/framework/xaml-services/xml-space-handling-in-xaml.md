---
title: Tratamento de xml:space em XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="1a1eb-102">Tratamento de xml:space em XAML</span><span class="sxs-lookup"><span data-stu-id="1a1eb-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="1a1eb-103">O `xml:space` é um atributo definido pelo XML que declara o comportamento de processamento de espaço em branco significativo dentro de um elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="1a1eb-103">The `xml:space` attribute is an XML-defined attribute that declares the significant whitespace processing behavior within an object element.</span></span> <span data-ttu-id="1a1eb-104">Esse comportamento é relevante para todo o conteúdo (texto interno) contido no elemento onde `xml:space` é declarado e também para elementos filho.</span><span class="sxs-lookup"><span data-stu-id="1a1eb-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1a1eb-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="1a1eb-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="1a1eb-106">\- ou -</span><span class="sxs-lookup"><span data-stu-id="1a1eb-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="1a1eb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a1eb-107">Remarks</span></span>  
 <span data-ttu-id="1a1eb-108">A definição para o `xml:space` atributo em XAML, incluindo seus dois valores possíveis é derivado de `xml:space` como definido como um "atributo especial" por especificações de W3C XML.</span><span class="sxs-lookup"><span data-stu-id="1a1eb-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="1a1eb-109">O valor padrão de `xml:space` atributo é o valor literal `"default"`.</span><span class="sxs-lookup"><span data-stu-id="1a1eb-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="1a1eb-110">Para o valor `"default"`, ou se `xml:space` não é indicado, o comportamento de análise de espaço em branco significativo é a manipulação do padrão, conforme definido no tópico [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1a1eb-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant whitespace parsing is the default handling, as defined in the topic [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="1a1eb-111">Para preservar espaço em branco dentro do conteúdo de elemento de objeto, especifique `xml:space="preserve"` naquele elemento.</span><span class="sxs-lookup"><span data-stu-id="1a1eb-111">To preserve whitespace within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="1a1eb-112">Na maioria dos interpretações, o `xml:space` efeitos de atributo e o valor do atributo passam para elementos filho.</span><span class="sxs-lookup"><span data-stu-id="1a1eb-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="1a1eb-113">Para obter uma discussão completa de espaços em branco em XAML de processamento, consulte [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1a1eb-113">For a complete discussion of whitespace processing in XAML, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1eb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a1eb-114">See Also</span></span>  
 [<span data-ttu-id="1a1eb-115">Processamento de Espaço em branco em XAML</span><span class="sxs-lookup"><span data-stu-id="1a1eb-115">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [<span data-ttu-id="1a1eb-116">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1a1eb-116">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
