---
title: "Extensão de marcação DynamicResource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f6c8500f9b9cd6d617789a2da3444519971ae81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="90087-102">Extensão de marcação DynamicResource</span><span class="sxs-lookup"><span data-stu-id="90087-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="90087-103">Fornece um valor para qualquer atributo da propriedade [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adiando esse valor para ser uma referência para um recurso definido.</span><span class="sxs-lookup"><span data-stu-id="90087-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="90087-104">O comportamento de pesquisa desse recurso é análogo à pesquisa em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="90087-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="90087-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="90087-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="90087-106">Uso do elemento propriedade XAML</span><span class="sxs-lookup"><span data-stu-id="90087-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="90087-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="90087-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="90087-108">A chave para o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="90087-108">The key for the requested resource.</span></span> <span data-ttu-id="90087-109">Essa chave foi inicialmente atribuída pelo [diretiva X:Key](../../../../docs/framework/xaml-services/x-key-directive.md) se um recurso foi criado na marcação ou foi fornecido como o `key` parâmetro ao chamar <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> se o recurso foi criado em código.</span><span class="sxs-lookup"><span data-stu-id="90087-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90087-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="90087-110">Remarks</span></span>  
 <span data-ttu-id="90087-111">Um `DynamicResource` criará uma expressão temporária durante a compilação inicial e, portanto, adiará a pesquisa por recursos até que o valor de recurso solicitado seja realmente necessário para construir um objeto.</span><span class="sxs-lookup"><span data-stu-id="90087-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="90087-112">Isso pode ocorrer após o carregamento da página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90087-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="90087-113">O valor do recurso será encontrado com base na pesquisa pela chave em todos os dicionários de recursos ativos, no escopo da página atual, e substituirá a expressão de espaço reservado da compilação.</span><span class="sxs-lookup"><span data-stu-id="90087-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90087-114">Em termos de precedência de propriedade de dependência, uma expressão `DynamicResource` é equivalente à posição em que a referência de recurso dinâmico é aplicada.</span><span class="sxs-lookup"><span data-stu-id="90087-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="90087-115">Se um valor local for definido para uma propriedade que tinha uma expressão `DynamicResource` como valor local anteriormente, o `DynamicResource` será totalmente removido.</span><span class="sxs-lookup"><span data-stu-id="90087-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="90087-116">Para obter mais detalhes, consulte [Precedência do valor da propriedade da dependência](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="90087-116">For details, see [Dependency Property Value Precedence](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="90087-117">Determinados cenários de acesso a recursos são particularmente apropriados para `DynamicResource`, ao contrário de uma [Extensão de Marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="90087-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span> <span data-ttu-id="90087-118">Consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) para ver uma discussão sobre os méritos relativos e as implicações de desempenho de `DynamicResource` e `StaticResource`.</span><span class="sxs-lookup"><span data-stu-id="90087-118">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="90087-119">Especificado <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> devem corresponder a um recurso existente determinado pelo [diretiva X:Key](../../../../docs/framework/xaml-services/x-key-directive.md) em algum nível na sua página, aplicativo, os temas de controle disponíveis e recursos externos ou recursos do sistema e o recurso de pesquisa ocorrerá nessa ordem.</span><span class="sxs-lookup"><span data-stu-id="90087-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="90087-120">Para obter mais informações sobre a pesquisa de recursos para recursos estáticos e dinâmicos, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="90087-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="90087-121">Uma chave de recurso pode ser qualquer cadeia de caracteres definida na [Gramática XamlName](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="90087-121">A resource key may be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="90087-122">Uma chave de recurso também pode ser outros tipos de objeto, como um <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="90087-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="90087-123">Um <xref:System.Type> chave é fundamental para como os controles podem ser estilizados por temas.</span><span class="sxs-lookup"><span data-stu-id="90087-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="90087-124">Para obter mais informações, consulte [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="90087-124">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<span data-ttu-id="90087-125">para a pesquisa de valores de recursos, tais como <xref:System.Windows.FrameworkElement.FindResource%2A>, seguem a mesma lógica de pesquisa de recursos usada por `DynamicResource`.</span><span class="sxs-lookup"><span data-stu-id="90087-125"> for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="90087-126">O meio declarativo alternativo de referenciar um recurso é como uma [Extensão de Marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="90087-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="90087-127">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="90087-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="90087-128">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `DynamicResource` é atribuído como o valor <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> da classe de extensão subjacente <xref:System.Windows.DynamicResourceExtension>.</span><span class="sxs-lookup"><span data-stu-id="90087-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="90087-129">`DynamicResource` pode ser usado na sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="90087-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="90087-130">Nesse caso, especificando o valor de <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="90087-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="90087-131">`DynamicResource` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> como sendo o par propriedade=valor:</span><span class="sxs-lookup"><span data-stu-id="90087-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="90087-132">O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais.</span><span class="sxs-lookup"><span data-stu-id="90087-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="90087-133">Como `DynamicResource` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.</span><span class="sxs-lookup"><span data-stu-id="90087-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="90087-134">No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação do processador, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.DynamicResourceExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="90087-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="90087-135">`DynamicResource` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="90087-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="90087-136">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="90087-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="90087-137">Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="90087-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="90087-138">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="90087-138">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90087-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90087-139">See Also</span></span>  
 [<span data-ttu-id="90087-140">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="90087-140">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="90087-141">Recursos e código</span><span class="sxs-lookup"><span data-stu-id="90087-141">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="90087-142">Diretiva x:Key</span><span class="sxs-lookup"><span data-stu-id="90087-142">x:Key Directive</span></span>](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [<span data-ttu-id="90087-143">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="90087-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="90087-144">Extensões de marcação e XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="90087-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="90087-145">Extensão de marcação StaticResource</span><span class="sxs-lookup"><span data-stu-id="90087-145">StaticResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [<span data-ttu-id="90087-146">Extensões de marcação e XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="90087-146">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
