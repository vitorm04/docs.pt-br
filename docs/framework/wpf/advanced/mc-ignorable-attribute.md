---
title: Atributo mc:Ignorable
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: e8fa4c084ae9c775a18de06c344b2c0b439c2b1b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467809"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="7145d-102">Atributo mc:Ignorable</span><span class="sxs-lookup"><span data-stu-id="7145d-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="7145d-103">Especifica quais prefixos do namespace [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] encontrados em um arquivo de marcação podem ser ignorados por um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7145d-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="7145d-104">O atributo `mc:Ignorable` dá suporte à compatibilidade de marcação para o mapeamento de namespace personalizado e para controle de versão de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7145d-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="7145d-105">Uso do atributo XAML (prefixo único)</span><span class="sxs-lookup"><span data-stu-id="7145d-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="7145d-106">Uso do atributo XAML (dois prefixos)</span><span class="sxs-lookup"><span data-stu-id="7145d-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7145d-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="7145d-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7145d-108">*ignorablePrefix, ignorablePrefix1, etc.*</span><span class="sxs-lookup"><span data-stu-id="7145d-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="7145d-109">Qualquer cadeia de caracteres de prefixo é válida, conforme a especificação de XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="7145d-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="7145d-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="7145d-110">*ignorableUri*</span></span>|<span data-ttu-id="7145d-111">Qualquer URI válido para designar um namespace, conforme a especificação XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="7145d-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="7145d-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="7145d-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="7145d-113">Um elemento que poderá ser ignorado por implementações do processador [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], se o tipo subjacente não puder ser resolvido.</span><span class="sxs-lookup"><span data-stu-id="7145d-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7145d-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7145d-114">Remarks</span></span>  
 <span data-ttu-id="7145d-115">O prefixo de namespace `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] é a convenção de prefixo recomendada a ser usada ao mapear o namespace de compatibilidade [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7145d-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="7145d-116">Elementos ou atributos em que a parte do prefixo do nome do elemento é identificado como `mc:Ignorable` não gerarão erros quando processados por um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7145d-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="7145d-117">Se esse atributo não puder ser resolvido para um tipo subjacente ou constructo de programação, esse elemento será ignorado.</span><span class="sxs-lookup"><span data-stu-id="7145d-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="7145d-118">No entanto, observe que elementos ignorados ainda podem gerar erros de análise adicionais para requisitos de elementos adicionais que são efeitos colaterais do elemento não estar sendo processado.</span><span class="sxs-lookup"><span data-stu-id="7145d-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="7145d-119">Por exemplo, um modelo de conteúdo do elemento específico pode requerer exatamente um elemento filho, porém, se o elemento filho especificado estava em um prefixo `mc:Ignorable` e o elemento filho especificado não pôde ser resolvido para um tipo, então o processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pode gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="7145d-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="7145d-120">`mc:Ignorable` aplica-se somente a mapeamentos de namespace para cadeias de caracteres de identificador.</span><span class="sxs-lookup"><span data-stu-id="7145d-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="7145d-121">`mc:Ignorable` não se aplica a mapeamentos de namespace em assemblies, que especificam um namespace e um assembly [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] (ou usam o executável atual como assembly por padrão).</span><span class="sxs-lookup"><span data-stu-id="7145d-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="7145d-122">Se você estiver implementando um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a implementação do processador não deverá gerar erros de análise ou de processamento na resolução de tipos para qualquer elemento ou atributo qualificado por um prefixo identificado como `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="7145d-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="7145d-123">Contudo, a implementação do processador pode, ainda assim, gerar exceções que são um resultado secundário da falha de um elemento ao carregar ou ser processado, como no exemplo de filho único fornecido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7145d-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="7145d-124">Por padrão, um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorará o conteúdo dentro de um elemento ignorado.</span><span class="sxs-lookup"><span data-stu-id="7145d-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="7145d-125">No entanto, você pode especificar um atributo adicional, [Atributo mc:ProcessContent](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), para exigir o processamento de conteúdo contínuo dentro de um elemento ignorado pelo próximo elemento pai disponível.</span><span class="sxs-lookup"><span data-stu-id="7145d-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="7145d-126">Vários prefixos podem ser especificados no atributo, usando um ou mais caracteres de espaço em branco como o separador, por exemplo: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="7145d-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="7145d-127">O namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] define outros elementos e atributos que não estão documentados dentro desta área do [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7145d-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="7145d-128">Para obter mais informações, consulte [Especificação de compatibilidade de marcação XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="7145d-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7145d-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7145d-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="7145d-130">Atributo PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="7145d-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="7145d-131">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7145d-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="7145d-132">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="7145d-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
