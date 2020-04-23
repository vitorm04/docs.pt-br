---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071440"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="8e96d-102">Tratamento de xml:lang em XAML</span><span class="sxs-lookup"><span data-stu-id="8e96d-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="8e96d-103">O `xml:lang` atributo é um atributo definido por XML que declara as informações de linguagem e cultura para um elemento em XML.</span><span class="sxs-lookup"><span data-stu-id="8e96d-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="8e96d-104">Este mesmo significado do atributo persiste em XAML; no entanto, algumas considerações adicionais se aplicam.</span><span class="sxs-lookup"><span data-stu-id="8e96d-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="8e96d-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="8e96d-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="8e96d-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="8e96d-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="8e96d-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="8e96d-107">*rfc3066lang*</span></span>|<span data-ttu-id="8e96d-108">Uma string que é derivada do padrão [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) e identifica uma língua ou uma região de idioma.</span><span class="sxs-lookup"><span data-stu-id="8e96d-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="8e96d-109">Quando é o último, a língua e a região são separadas por um único hífen.</span><span class="sxs-lookup"><span data-stu-id="8e96d-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="8e96d-110">Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e formato.</span><span class="sxs-lookup"><span data-stu-id="8e96d-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e96d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e96d-111">Remarks</span></span>

<span data-ttu-id="8e96d-112">A definição `xml:lang` para [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] o atributo `xml:lang` em é derivada como um "atributo especial" pelo World Wide Web Consortium (W3C) para XML.</span><span class="sxs-lookup"><span data-stu-id="8e96d-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="8e96d-113">As informações de linguagem e cultura são potencialmente processadas de diferentes formas por elementos, dependendo de suas implementações; no entanto, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] não há `xml:lang` processamento padrão do atributo.</span><span class="sxs-lookup"><span data-stu-id="8e96d-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="8e96d-114">O valor padrão `xml:lang` do atributo é uma seqüência de string vazia no nível de atributo.</span><span class="sxs-lookup"><span data-stu-id="8e96d-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="8e96d-115">Os `xml:lang` efeitos atributos e o valor do atributo são geralmente perpetuados `xml:lang` aos elementos infantis, quando interpretados por sistemas que atuam sobre valores.</span><span class="sxs-lookup"><span data-stu-id="8e96d-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="8e96d-116">Quando interpretado por escritores XAML de .NET XAML Services, um `xml:lang` valor pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos na representação de objeto subjacente; no entanto, esse comportamento depende se `xml:lang` o valor especificado é uma construção válida para essas classes.</span><span class="sxs-lookup"><span data-stu-id="8e96d-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="8e96d-117">Os frameworks podem criar associações entre propriedades `xml:lang` definidas por <xref:System.Windows.Markup.XmlLangPropertyAttribute> framework e o significado de em XML aplicando-se à propriedade.</span><span class="sxs-lookup"><span data-stu-id="8e96d-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="8e96d-118">Dedos de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="8e96d-118">WPF Usage Nodes</span></span>

<span data-ttu-id="8e96d-119">Para elementos que são <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>classes derivadas de <xref:System.Windows.FrameworkElement.Language%2A> ou , você `xml:lang` pode usar a propriedade de dependência equivalente em vez do atributo.</span><span class="sxs-lookup"><span data-stu-id="8e96d-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="8e96d-120">Por padrão, <xref:System.Windows.FrameworkElement.Language%2A> a propriedade usa "en-US" se não for definida de outra `xml:lang` forma, seja através da propriedade ou através do processamento do atributo.</span><span class="sxs-lookup"><span data-stu-id="8e96d-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e96d-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e96d-121">See also</span></span>

- [<span data-ttu-id="8e96d-122">Globalização do WPF</span><span class="sxs-lookup"><span data-stu-id="8e96d-122">Globalization for WPF</span></span>](../../framework/wpf/advanced/globalization-for-wpf.md)
