---
title: "Extensão de marcação ThemeDictionary"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2372961cdc889528f13e13dd1f1760608030275e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="9207a-102">Extensão de marcação ThemeDictionary</span><span class="sxs-lookup"><span data-stu-id="9207a-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="9207a-103">Fornece uma maneira para autores de controles personalizados ou aplicativos que integram controles de terceiros de carregar os dicionários de recursos específicos de temas para uso ao aplicar estilo ao controle.</span><span class="sxs-lookup"><span data-stu-id="9207a-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="9207a-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="9207a-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="9207a-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="9207a-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9207a-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="9207a-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="9207a-107">O [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] do assembly que contém informações de tema.</span><span class="sxs-lookup"><span data-stu-id="9207a-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="9207a-108">Normalmente, esse é um URI "pack://" que referencia um assembly no pacote maior.</span><span class="sxs-lookup"><span data-stu-id="9207a-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="9207a-109">Recursos de assembly e URIs "pack://" simplificam os problemas de implantação.</span><span class="sxs-lookup"><span data-stu-id="9207a-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="9207a-110">Para obter mais informações, consulte [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="9207a-110">For more information see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9207a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9207a-111">Remarks</span></span>  
 <span data-ttu-id="9207a-112">Essa extensão destina-se a preencher apenas uma valor de propriedade específico: um valor para <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9207a-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9207a-113">Usando essa extensão, você pode especificar um único assembly apenas de recursos que contém alguns estilos a serem usados somente quando o tema [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] é aplicado ao sistema do usuário, outros estilos quando o tema Luna estiver ativo, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9207a-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="9207a-114">Usando essa extensão, o conteúdo de um dicionário de recursos específico do controle pode ser invalidado e recarregado automaticamente para ser específico para outro tema quando necessário.</span><span class="sxs-lookup"><span data-stu-id="9207a-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="9207a-115">O `assemblyUri` cadeia de caracteres (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> valor da propriedade) constitui a base de uma convenção de nomenclatura que identifica qual dicionário aplica-se a um tema específico.</span><span class="sxs-lookup"><span data-stu-id="9207a-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="9207a-116">O <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> lógica para `ThemeDictionary` conclui a convenção por gerar um [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] que aponta para uma variante do dicionário de tema específico, como contido em um assembly de recursos pré-compilado.</span><span class="sxs-lookup"><span data-stu-id="9207a-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="9207a-117">A descrição dessa convenção, ou as interações dos temas com estilos gerais de controle e estilos de nível de página/aplicativo como um conceito não é abordado completamente aqui.</span><span class="sxs-lookup"><span data-stu-id="9207a-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="9207a-118">O cenário básico para uso `ThemeDictionary` é especificar o <xref:System.Windows.ResourceDictionary.Source%2A> propriedade de um `ResourceDictionary` declarado no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9207a-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="9207a-119">Quando você fornece um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o assembly por meio de uma extensão `ThemeDictionary` em vez de um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] direto, a lógica da extensão fornecerá lógica de invalidação que se aplica sempre que o tema do sistema for alterado.</span><span class="sxs-lookup"><span data-stu-id="9207a-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="9207a-120">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="9207a-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="9207a-121">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `ThemeDictionary` é atribuído como o valor <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> da classe de extensão subjacente <xref:System.Windows.ThemeDictionaryExtension>.</span><span class="sxs-lookup"><span data-stu-id="9207a-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="9207a-122">`ThemeDictionary` também pode ser usado na sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="9207a-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="9207a-123">Nesse caso, especificando o valor de <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="9207a-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="9207a-124">`ThemeDictionary` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.Markup.StaticExtension.Member%2A> como sendo o par propriedade=valor:</span><span class="sxs-lookup"><span data-stu-id="9207a-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="9207a-125">O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais.</span><span class="sxs-lookup"><span data-stu-id="9207a-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="9207a-126">Como `ThemeDictionary` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.</span><span class="sxs-lookup"><span data-stu-id="9207a-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="9207a-127">No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação do processador, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.ThemeDictionaryExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="9207a-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="9207a-128">`ThemeDictionary` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="9207a-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="9207a-129">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="9207a-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="9207a-130">Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="9207a-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="9207a-131">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="9207a-131">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9207a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9207a-132">See Also</span></span>  
 [<span data-ttu-id="9207a-133">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="9207a-133">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="9207a-134">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="9207a-134">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="9207a-135">Extensões de marcação e XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="9207a-135">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="9207a-136">Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF</span><span class="sxs-lookup"><span data-stu-id="9207a-136">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
