---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b3f236b2378d6af78f034856e3ba0f7a9e17993c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837136"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="94901-102">Tratamento de xml:lang em XAML</span><span class="sxs-lookup"><span data-stu-id="94901-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="94901-103">O atributo `xml:lang` é um atributo definido por XML que declara as informações de idioma e cultura de um elemento em XML.</span><span class="sxs-lookup"><span data-stu-id="94901-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="94901-104">Esse mesmo significado do atributo persiste em XAML; no entanto, algumas considerações adicionais se aplicam.</span><span class="sxs-lookup"><span data-stu-id="94901-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="94901-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="94901-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="94901-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="94901-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94901-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="94901-107">*rfc3066lang*</span></span>|<span data-ttu-id="94901-108">Uma cadeia de caracteres que é derivada do padrão [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) e identifica um idioma ou uma região de idioma.</span><span class="sxs-lookup"><span data-stu-id="94901-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="94901-109">Quando é o último, o idioma e a região são separados por um único hífen.</span><span class="sxs-lookup"><span data-stu-id="94901-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="94901-110">Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e o formato.</span><span class="sxs-lookup"><span data-stu-id="94901-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94901-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="94901-111">Remarks</span></span>  
 <span data-ttu-id="94901-112">A definição do atributo `xml:lang` no [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é derivada de `xml:lang` conforme definido como um "atributo especial" pelo World Wide Web Consortium (W3C) for XML.</span><span class="sxs-lookup"><span data-stu-id="94901-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="94901-113">As informações de linguagem e cultura são potencialmente processadas de maneiras diferentes por elementos, dependendo de suas implementações; no entanto, não há nenhum [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processamento padrão do atributo `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="94901-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="94901-114">O valor padrão do atributo `xml:lang` é uma cadeia de caracteres vazia no nível de atributo.</span><span class="sxs-lookup"><span data-stu-id="94901-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="94901-115">Os efeitos de atributo `xml:lang` e o valor do atributo são geralmente perpetuados para elementos filho, quando interpretados por sistemas que atuam em valores `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="94901-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="94901-116">Quando interpretado por gravadores XAML de .NET Framework serviços XAML, um valor de `xml:lang` pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos na representação de objeto subjacente; no entanto, esse comportamento depende se o valor especificado para `xml:lang` é uma construção válida para essas classes.</span><span class="sxs-lookup"><span data-stu-id="94901-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="94901-117">As estruturas podem criar associações entre propriedades definidas pela estrutura e o significado de `xml:lang` em XML aplicando <xref:System.Windows.Markup.XmlLangPropertyAttribute> à propriedade.</span><span class="sxs-lookup"><span data-stu-id="94901-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="94901-118">Nós de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="94901-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="94901-119">Para elementos que são classes derivadas de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, você pode usar a propriedade de dependência <xref:System.Windows.FrameworkElement.Language%2A> equivalente em vez do atributo de `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="94901-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="94901-120">Por padrão, a propriedade <xref:System.Windows.FrameworkElement.Language%2A> usa "en-US" se não for definida de outra forma, por meio da propriedade ou pelo processamento do atributo `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="94901-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94901-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94901-121">See also</span></span>

- [<span data-ttu-id="94901-122">Globalização para WPF</span><span class="sxs-lookup"><span data-stu-id="94901-122">Globalization for WPF</span></span>](../wpf/advanced/globalization-for-wpf.md)
