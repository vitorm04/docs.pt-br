---
title: Extensão de marcação ThemeDictionary
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: f6ba0fe45aa11063c79d673b26794072968f4200
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646183"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="7c9b7-102">Extensão de marcação ThemeDictionary</span><span class="sxs-lookup"><span data-stu-id="7c9b7-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="7c9b7-103">Fornece uma maneira para autores de controles personalizados ou aplicativos que integram controles de terceiros de carregar os dicionários de recursos específicos de temas para uso ao aplicar estilo ao controle.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="7c9b7-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="7c9b7-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="7c9b7-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="7c9b7-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7c9b7-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="7c9b7-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="7c9b7-107">O identificador de recursos uniforme (URI) do conjunto que contém informações temáticas.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-107">The uniform resource identifier (URI) of the assembly that contains theme information.</span></span> <span data-ttu-id="7c9b7-108">Normalmente, esse é um URI "pack://" que referencia um assembly no pacote maior.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="7c9b7-109">Recursos de assembly e URIs "pack://" simplificam os problemas de implantação.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="7c9b7-110">Para obter mais informações, consulte [Pack URIs no WPF](../app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="7c9b7-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9b7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c9b7-111">Remarks</span></span>  
 <span data-ttu-id="7c9b7-112">Esta extensão destina-se a preencher apenas <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>um valor específico de propriedade: um valor para .</span><span class="sxs-lookup"><span data-stu-id="7c9b7-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7c9b7-113">Usando esta extensão, você pode especificar um único conjunto somente de recursos que contém alguns estilos para usar somente quando o tema do Windows Aero é aplicado ao sistema do usuário, outros estilos somente quando o tema Luna estiver ativo, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="7c9b7-114">Usando essa extensão, o conteúdo de um dicionário de recursos específico do controle pode ser invalidado e recarregado automaticamente para ser específico para outro tema quando necessário.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="7c9b7-115">A `assemblyUri` string<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> (valor da propriedade) forma a base de uma convenção de nomeação que identifica qual dicionário se aplica a um determinado tema.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="7c9b7-116">A <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> lógica `ThemeDictionary` para concluir a convenção gerando um identificador de recursos uniforme (URI) que aponta para uma variante específica do dicionário temático, contido em uma montagem de recursos pré-compilada.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a uniform resource identifier (URI) that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="7c9b7-117">A descrição dessa convenção, ou as interações dos temas com estilos gerais de controle e estilos de nível de página/aplicativo como um conceito não é abordado completamente aqui.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="7c9b7-118">O cenário básico `ThemeDictionary` para usar <xref:System.Windows.ResourceDictionary.Source%2A> é `ResourceDictionary` especificar a propriedade de um declarado no nível de aplicação.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="7c9b7-119">Quando você fornece um URI `ThemeDictionary` para a montagem através de uma extensão e não como um URI direto, a lógica de extensão fornecerá lógica de invalidação que se aplica sempre que o tema do sistema mudar.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-119">When you provide a URI for the assembly through a `ThemeDictionary` extension rather than as a direct URI, the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="7c9b7-120">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="7c9b7-121">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `ThemeDictionary` é atribuído como o valor <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> da classe de extensão subjacente <xref:System.Windows.ThemeDictionaryExtension>.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="7c9b7-122">`ThemeDictionary` também pode ser usado na sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="7c9b7-123">Neste caso, é necessário especificar o valor da <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="7c9b7-124">`ThemeDictionary` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.Markup.StaticExtension.Member%2A> como sendo o par propriedade=valor:</span><span class="sxs-lookup"><span data-stu-id="7c9b7-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="7c9b7-125">O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="7c9b7-126">Como `ThemeDictionary` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="7c9b7-127">Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação do processador, o manuseio para esta <xref:System.Windows.ThemeDictionaryExtension> extensão de marcação é definido pela classe.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="7c9b7-128">`ThemeDictionary` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="7c9b7-129">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="7c9b7-130">Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="7c9b7-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="7c9b7-131">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="7c9b7-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9b7-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="7c9b7-132">See also</span></span>

- [<span data-ttu-id="7c9b7-133">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="7c9b7-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7c9b7-134">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7c9b7-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="7c9b7-135">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="7c9b7-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="7c9b7-136">Arquivos de recurso, conteúdo e dados do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="7c9b7-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
