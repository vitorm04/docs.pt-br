---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 886f4063fa8c793fdce93431a29219cf86078593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562018"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="0801e-102">Tratamento de xml:lang em XAML</span><span class="sxs-lookup"><span data-stu-id="0801e-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="0801e-103">O `xml:lang` atributo é um [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-atributo definido que declara informações de idioma e cultura para um elemento no XML.</span><span class="sxs-lookup"><span data-stu-id="0801e-103">The `xml:lang` attribute is an [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="0801e-104">O mesmo significado do atributo persiste no XAML; No entanto, algumas considerações adicionais se aplicam.</span><span class="sxs-lookup"><span data-stu-id="0801e-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="0801e-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="0801e-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="0801e-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="0801e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0801e-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="0801e-107">*rfc3066lang*</span></span>|<span data-ttu-id="0801e-108">Uma cadeia de caracteres que é derivada de [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) padrão e identifica um idioma ou uma região de idioma.</span><span class="sxs-lookup"><span data-stu-id="0801e-108">A string that is derived from the [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="0801e-109">Quando for o último, o idioma e região são separados por um hífen.</span><span class="sxs-lookup"><span data-stu-id="0801e-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="0801e-110">Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e o formato.</span><span class="sxs-lookup"><span data-stu-id="0801e-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0801e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0801e-111">Remarks</span></span>  
 <span data-ttu-id="0801e-112">A definição para o `xml:lang` atributo [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é derivado do `xml:lang` como definido como um "atributo especial" pelo [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] para [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0801e-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] for [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span></span> <span data-ttu-id="0801e-113">Informações de idioma e cultura pode ser processadas de diferentes maneiras por elementos, dependendo de suas implementações; No entanto, não há nenhum padrão [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] o processamento do `xml:lang` atributo.</span><span class="sxs-lookup"><span data-stu-id="0801e-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="0801e-114">O valor padrão de `xml:lang` atributo é uma cadeia de caracteres vazia no nível do atributo.</span><span class="sxs-lookup"><span data-stu-id="0801e-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="0801e-115">O `xml:lang` efeitos de atributo e o valor do atributo em geral são preservadas em elementos filho, interpretado pelos sistemas que atuam em `xml:lang` valores.</span><span class="sxs-lookup"><span data-stu-id="0801e-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="0801e-116">Interpretado pelos autores XAML de serviços XAML do .NET Framework, um `xml:lang` valor pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos subjacentes do objeto representação; no entanto, esse comportamento depende de se o valor especificado para `xml:lang`é uma construção válida para essas classes.</span><span class="sxs-lookup"><span data-stu-id="0801e-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="0801e-117">Estruturas podem criar associações entre propriedades definidas pelo framework e o significado de `xml:lang` em XML, aplicando <xref:System.Windows.Markup.XmlLangPropertyAttribute> à propriedade.</span><span class="sxs-lookup"><span data-stu-id="0801e-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="0801e-118">Nós de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="0801e-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="0801e-119">Para elementos que são classes derivadas de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, você pode usar o equivalente <xref:System.Windows.FrameworkElement.Language%2A> propriedade de dependência em vez do `xml:lang` atributo.</span><span class="sxs-lookup"><span data-stu-id="0801e-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="0801e-120">Por padrão, o <xref:System.Windows.FrameworkElement.Language%2A> propriedade usa "en-US" se ele não é for definido, por meio da propriedade ou por meio do processamento de `xml:lang` atributo.</span><span class="sxs-lookup"><span data-stu-id="0801e-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0801e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0801e-121">See Also</span></span>  
 [<span data-ttu-id="0801e-122">Globalização para WPF</span><span class="sxs-lookup"><span data-stu-id="0801e-122">Globalization for WPF</span></span>](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
