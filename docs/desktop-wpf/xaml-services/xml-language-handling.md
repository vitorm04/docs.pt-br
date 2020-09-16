---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 92d1eda62ff394df54d9607bab46d9950681e603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548202"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="fb448-102">Tratamento de xml:lang em XAML</span><span class="sxs-lookup"><span data-stu-id="fb448-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="fb448-103">O `xml:lang` atributo é um atributo definido por XML que declara as informações de idioma e cultura de um elemento em XML.</span><span class="sxs-lookup"><span data-stu-id="fb448-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="fb448-104">Esse mesmo significado do atributo persiste em XAML; no entanto, algumas considerações adicionais se aplicam.</span><span class="sxs-lookup"><span data-stu-id="fb448-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="fb448-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="fb448-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="fb448-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="fb448-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="fb448-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="fb448-107">*rfc3066lang*</span></span>|<span data-ttu-id="fb448-108">Uma cadeia de caracteres que é derivada do padrão [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) e identifica um idioma ou uma região de idioma.</span><span class="sxs-lookup"><span data-stu-id="fb448-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="fb448-109">Quando é o último, o idioma e a região são separados por um único hífen.</span><span class="sxs-lookup"><span data-stu-id="fb448-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="fb448-110">Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e o formato.</span><span class="sxs-lookup"><span data-stu-id="fb448-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fb448-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb448-111">Remarks</span></span>

<span data-ttu-id="fb448-112">A definição para o `xml:lang` atributo no [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é derivada de `xml:lang` conforme definido como um "atributo especial" pelo World Wide Web Consortium (W3C) para XML.</span><span class="sxs-lookup"><span data-stu-id="fb448-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="fb448-113">As informações de linguagem e cultura são potencialmente processadas de maneiras diferentes por elementos, dependendo de suas implementações; no entanto, não há nenhum [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processamento padrão do `xml:lang` atributo.</span><span class="sxs-lookup"><span data-stu-id="fb448-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="fb448-114">O valor padrão do `xml:lang` atributo é uma cadeia de caracteres vazia no nível de atributo.</span><span class="sxs-lookup"><span data-stu-id="fb448-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="fb448-115">Os `xml:lang` efeitos de atributo e o valor do atributo são geralmente perpetuais para elementos filho, quando interpretados por sistemas que atuam em `xml:lang` valores.</span><span class="sxs-lookup"><span data-stu-id="fb448-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="fb448-116">Quando interpretado por gravadores XAML dos serviços XAML .NET, um `xml:lang` valor pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos na representação de objeto subjacente; no entanto, esse comportamento depende se o valor especificado para `xml:lang` é uma construção válida para essas classes.</span><span class="sxs-lookup"><span data-stu-id="fb448-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="fb448-117">As estruturas podem criar associações entre propriedades definidas pela estrutura e o significado de `xml:lang` em XML aplicando- <xref:System.Windows.Markup.XmlLangPropertyAttribute> se à propriedade.</span><span class="sxs-lookup"><span data-stu-id="fb448-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="fb448-118">Nós de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="fb448-118">WPF Usage Nodes</span></span>

<span data-ttu-id="fb448-119">Para elementos que são classes derivadas de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> , você pode usar a <xref:System.Windows.FrameworkElement.Language%2A> propriedade de dependência equivalente em vez do `xml:lang` atributo.</span><span class="sxs-lookup"><span data-stu-id="fb448-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="fb448-120">Por padrão, a <xref:System.Windows.FrameworkElement.Language%2A> propriedade usa "en-US" se não for definida de outra forma, por meio da propriedade ou pelo processamento do `xml:lang` atributo.</span><span class="sxs-lookup"><span data-stu-id="fb448-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb448-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb448-121">See also</span></span>

- [<span data-ttu-id="fb448-122">Globalização do WPF</span><span class="sxs-lookup"><span data-stu-id="fb448-122">Globalization for WPF</span></span>](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
