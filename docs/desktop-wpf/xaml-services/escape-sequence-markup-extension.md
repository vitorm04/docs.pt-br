---
title: '{}Seqüência de fuga - Extensão de marcação'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071741"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="08ef0-102">{}Extensão de seqüência de fuga / extensão de marcação</span><span class="sxs-lookup"><span data-stu-id="08ef0-102">{} Escape sequence / markup extension</span></span>

<span data-ttu-id="08ef0-103">Fornece a seqüência de fuga XAML para valores de atributo.</span><span class="sxs-lookup"><span data-stu-id="08ef0-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="08ef0-104">A seqüência de fuga permite que os valores subseqüentes no atributo sejam interpretados como literal.</span><span class="sxs-lookup"><span data-stu-id="08ef0-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="08ef0-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="08ef0-105">XAML Attribute Usage</span></span>

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a><span data-ttu-id="08ef0-106">Uso do elemento propriedade XAML</span><span class="sxs-lookup"><span data-stu-id="08ef0-106">XAML Property Element Usage</span></span>

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="08ef0-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="08ef0-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="08ef0-108">*literalValor*</span><span class="sxs-lookup"><span data-stu-id="08ef0-108">*literalValue*</span></span>|<span data-ttu-id="08ef0-109">A seqüência literal que segue a seqüência de fuga.</span><span class="sxs-lookup"><span data-stu-id="08ef0-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="08ef0-110">Normalmente, esta seqüência contém uma cinta aberta ou fechada ({ ou }).</span><span class="sxs-lookup"><span data-stu-id="08ef0-110">Typically this string contains an open or close brace ({ or }).</span></span>|

## <a name="remarks"></a><span data-ttu-id="08ef0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="08ef0-111">Remarks</span></span>

<span data-ttu-id="08ef0-112">A seqüência de fuga ({}) é usada para que uma cinta aberta ({) possa ser usada como um caractere literal em XAML.</span><span class="sxs-lookup"><span data-stu-id="08ef0-112">The escape sequence ({}) is used so that an open brace ({) can be used as a literal character in XAML.</span></span>

<span data-ttu-id="08ef0-113">Os leitores XAML normalmente usam a cinta aberta ({) para denotar o ponto de entrada de uma extensão de marcação; no entanto, primeiro verificam o próximo caractere para determinar se é uma cinta de fechamento (}).</span><span class="sxs-lookup"><span data-stu-id="08ef0-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="08ef0-114">Somente quando as duas{}chaves são adjacentes, são consideradas uma seqüência de fuga.</span><span class="sxs-lookup"><span data-stu-id="08ef0-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>

<span data-ttu-id="08ef0-115">Se a seqüência de fuga for encontrada, o leitor XAML deve processar o restante da seqüência como uma string.</span><span class="sxs-lookup"><span data-stu-id="08ef0-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="08ef0-116">No entanto, se a seqüência de fuga for aplicada a um membro que tenha um conversor de tipo, a string pode sofrer conversão de tipo quando for interpretada por um escritor XAML.</span><span class="sxs-lookup"><span data-stu-id="08ef0-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>

<span data-ttu-id="08ef0-117">A seqüência de escape não é uma extensão de marcação e não é apoiada por uma classe.</span><span class="sxs-lookup"><span data-stu-id="08ef0-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="08ef0-118">No entanto, é uma convenção que os leitores XAML (incluindo leitores XAML personalizados) devem respeitar.</span><span class="sxs-lookup"><span data-stu-id="08ef0-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>

<span data-ttu-id="08ef0-119">Uma marca de cotação (") não pode ser usada como uma seqüência de fuga desta maneira.</span><span class="sxs-lookup"><span data-stu-id="08ef0-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="08ef0-120">Se você precisar definir uma marca de cotação como um valor de propriedade para uma propriedade não contente, use a sintaxe do elemento de propriedade e coloque a marca de cotação como uma string dentro do elemento de propriedade ou use uma entidade de caractere XML.</span><span class="sxs-lookup"><span data-stu-id="08ef0-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="08ef0-121">Para uma propriedade de conteúdo, a marca de cotação pode ser todo o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="08ef0-121">For a content property, the quotation mark can be the entire content.</span></span>

<span data-ttu-id="08ef0-122">A seqüência de fuga ({}) é freqüentemente necessária ao especificar um tipo XML que deve incluir um qualificador de namespace em um local onde uma extensão de marcação XAML pode aparecer.</span><span class="sxs-lookup"><span data-stu-id="08ef0-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="08ef0-123">Este local inclui o início de um valor de atributo XAML e em uma extensão de marcação imediatamente após um sinal igual (=).</span><span class="sxs-lookup"><span data-stu-id="08ef0-123">This location includes the start of a XAML attribute value, and in a markup extension immediately after an equal sign (=).</span></span> <span data-ttu-id="08ef0-124">O exemplo a seguir mostra seqüências de fuga para um namespace XML que aparece no início de um valor de atributo XAML.</span><span class="sxs-lookup"><span data-stu-id="08ef0-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a><span data-ttu-id="08ef0-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="08ef0-125">See also</span></span>

- [<span data-ttu-id="08ef0-126">Conversores de tipo e extensões de marcação para XAML</span><span class="sxs-lookup"><span data-stu-id="08ef0-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions.md)
- [<span data-ttu-id="08ef0-127">Entidades e XAML de caractere XML</span><span class="sxs-lookup"><span data-stu-id="08ef0-127">XML Character Entities and XAML</span></span>](xml-character-entities.md)
