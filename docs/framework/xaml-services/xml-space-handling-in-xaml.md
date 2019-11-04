---
title: Tratamento de xml:space em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458797"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="b04d5-102">Tratamento de xml:space em XAML</span><span class="sxs-lookup"><span data-stu-id="b04d5-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="b04d5-103">O atributo `xml:space` é um atributo definido por XML que declara o comportamento significativo de processamento de espaço em branco dentro de um elemento Object.</span><span class="sxs-lookup"><span data-stu-id="b04d5-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="b04d5-104">Esse comportamento é relevante para todo o conteúdo (texto interno) contido no elemento em que `xml:space` é declarado, além de escopos para elementos filho.</span><span class="sxs-lookup"><span data-stu-id="b04d5-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b04d5-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="b04d5-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="b04d5-106">\- ou -</span><span class="sxs-lookup"><span data-stu-id="b04d5-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="b04d5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b04d5-107">Remarks</span></span>  
 <span data-ttu-id="b04d5-108">A definição para o atributo `xml:space` em XAML, incluindo seus dois valores possíveis, é derivada de `xml:space` conforme definido como um "atributo especial" pelas especificações do W3C para XML.</span><span class="sxs-lookup"><span data-stu-id="b04d5-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="b04d5-109">O valor padrão do atributo `xml:space` é o valor literal `"default"`.</span><span class="sxs-lookup"><span data-stu-id="b04d5-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="b04d5-110">Para o valor `"default"`, ou se `xml:space` não for indicado, o comportamento da análise de espaço em branco significativa é o tratamento padrão, conforme definido no tópico [processamento de espaço em branco em XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b04d5-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="b04d5-111">Para preservar o espaço em branco no conteúdo do elemento de objeto, especifique `xml:space="preserve"` nesse elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="b04d5-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="b04d5-112">Na maioria das interpretações, os efeitos de atributo `xml:space` e o valor do atributo têm como escopo os elementos filho.</span><span class="sxs-lookup"><span data-stu-id="b04d5-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="b04d5-113">Para obter uma discussão completa sobre o processamento de espaço em branco em XAML, consulte [processamento de espaço em branco em XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b04d5-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04d5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b04d5-114">See also</span></span>

- [<span data-ttu-id="b04d5-115">Processamento de espaço em branco em XAML</span><span class="sxs-lookup"><span data-stu-id="b04d5-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="b04d5-116">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="b04d5-116">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
