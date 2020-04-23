---
title: Tratamento de xml:space em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071433"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="0d6f0-102">Tratamento de xml:space em XAML</span><span class="sxs-lookup"><span data-stu-id="0d6f0-102">xml:space Handling in XAML</span></span>

<span data-ttu-id="0d6f0-103">O `xml:space` atributo é um atributo definido por XML que declara o comportamento significativo de processamento de espaço branco dentro de um elemento objeto.</span><span class="sxs-lookup"><span data-stu-id="0d6f0-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="0d6f0-104">Esse comportamento é relevante para todo o conteúdo `xml:space` (texto interno) contido no elemento onde é declarado, e também escopos para elementos infantis.</span><span class="sxs-lookup"><span data-stu-id="0d6f0-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="0d6f0-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="0d6f0-105">XAML Attribute Usage</span></span>

```xaml
<object xml:space="preserve" />
```

 <span data-ttu-id="0d6f0-106">\- ou –</span><span class="sxs-lookup"><span data-stu-id="0d6f0-106">\- or -</span></span>

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a><span data-ttu-id="0d6f0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d6f0-107">Remarks</span></span>

<span data-ttu-id="0d6f0-108">A definição `xml:space` para o atributo em XAML, `xml:space` incluindo seus dois valores possíveis, é derivada de como definido como um "atributo especial" pelas especificações W3C para XML.</span><span class="sxs-lookup"><span data-stu-id="0d6f0-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>

<span data-ttu-id="0d6f0-109">O valor padrão `xml:space` do atributo `"default"`é o valor literal.</span><span class="sxs-lookup"><span data-stu-id="0d6f0-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="0d6f0-110">Para o `"default"`valor `xml:space` , ou se não for indicado, o comportamento de análise significativa do espaço branco é o manuseio padrão, conforme definido no tópico [Processamento de espaço branco em XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="0d6f0-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](white-space-processing.md).</span></span>

<span data-ttu-id="0d6f0-111">Para preservar o espaço em `xml:space="preserve"` branco dentro do conteúdo do elemento objeto, especifique nesse elemento do objeto.</span><span class="sxs-lookup"><span data-stu-id="0d6f0-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>

<span data-ttu-id="0d6f0-112">Na maioria das `xml:space` interpretações, os efeitos atributos e o valor do atributo são escopo de elementos infantis.</span><span class="sxs-lookup"><span data-stu-id="0d6f0-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>

<span data-ttu-id="0d6f0-113">Para uma discussão completa sobre o processamento do espaço branco em XAML, consulte [o processamento de espaço branco em XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="0d6f0-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](white-space-processing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d6f0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d6f0-114">See also</span></span>

- [<span data-ttu-id="0d6f0-115">Processamento de espaço em branco em XAML</span><span class="sxs-lookup"><span data-stu-id="0d6f0-115">White-space processing in XAML</span></span>](white-space-processing.md)
- [<span data-ttu-id="0d6f0-116">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="0d6f0-116">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
