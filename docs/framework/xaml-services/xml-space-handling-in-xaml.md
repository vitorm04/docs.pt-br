---
title: Tratamento de xml:space em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: d15bab1ad9234959048fa7b7c3fa2bbbeca5fe6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193311"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="79709-102">Tratamento de xml:space em XAML</span><span class="sxs-lookup"><span data-stu-id="79709-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="79709-103">O `xml:space` é um atributo definido pelo XML que declara o comportamento de processamento significativo de espaço em branco dentro de um elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="79709-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="79709-104">Esse comportamento é relevante para todo o conteúdo (texto interno) contido no elemento onde `xml:space` é declarada e também para os elementos filho.</span><span class="sxs-lookup"><span data-stu-id="79709-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="79709-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="79709-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="79709-106">\- ou -</span><span class="sxs-lookup"><span data-stu-id="79709-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="79709-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="79709-107">Remarks</span></span>  
 <span data-ttu-id="79709-108">A definição para o `xml:space` atributo no XAML, incluindo seus dois valores possíveis é derivado de `xml:space` conforme definido como um "atributo especial" pelas especificações de W3C para XML.</span><span class="sxs-lookup"><span data-stu-id="79709-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="79709-109">O valor padrão de `xml:space` atributo é o valor literal `"default"`.</span><span class="sxs-lookup"><span data-stu-id="79709-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="79709-110">Para o valor `"default"`, ou se `xml:space` não é indicado, o comportamento de análise de espaço em branco significativo é a manipulação de padrão, conforme definido no tópico [XAML de processamento de espaço em branco](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="79709-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="79709-111">Para preservar espaço em branco dentro do conteúdo de elemento de objeto, especifique `xml:space="preserve"` nesse elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="79709-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="79709-112">Na maioria dos interpretações, o `xml:space` efeitos do atributo e o valor do atributo limitam-se aos elementos filho.</span><span class="sxs-lookup"><span data-stu-id="79709-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="79709-113">Para obter uma discussão completa sobre o espaço em branco em XAML de processamento, consulte [XAML de processamento de espaço em branco](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="79709-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79709-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79709-114">See also</span></span>

- [<span data-ttu-id="79709-115">Processamento de espaço em branco em XAML</span><span class="sxs-lookup"><span data-stu-id="79709-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="79709-116">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="79709-116">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
