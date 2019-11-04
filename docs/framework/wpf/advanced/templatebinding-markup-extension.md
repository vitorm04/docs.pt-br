---
title: Extensão de marcação TemplateBinding
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458661"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="f5cf4-102">Extensão de marcação TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="f5cf4-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="f5cf4-103">Vincula o valor de uma propriedade em um modelo de controle para ser o valor de outra propriedade no controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f5cf4-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="f5cf4-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="f5cf4-105">Uso do Atributo XAML (para propriedade Setter em um modelo ou estilo)</span><span class="sxs-lookup"><span data-stu-id="f5cf4-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f5cf4-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="f5cf4-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="f5cf4-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> da propriedade sendo definida na sintaxe setter.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="f5cf4-108">Outra propriedade de dependência que existe no tipo que está sendo personalizado, especificada por <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="f5cf4-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="f5cf4-109">- or -</span></span><br /><br /> <span data-ttu-id="f5cf4-110">Um nome de propriedade "pontilhado" definido por um tipo diferente do tipo de destino sendo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="f5cf4-111">Isso é, na verdade, um <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="f5cf4-112">Consulte [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="f5cf4-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5cf4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5cf4-113">Remarks</span></span>  
 <span data-ttu-id="f5cf4-114">Uma `TemplateBinding` é uma forma otimizada de uma [Associação](binding-markup-extension.md) para cenários de modelo, análoga a um `Binding` construído com `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="f5cf4-115">Um `TemplateBinding` é sempre uma associação unidirecional, mesmo se as propriedades envolverem associação bidirecional padrão.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="f5cf4-116">Ambas as propriedades envolvidas devem ser propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="f5cf4-117">Para obter uma ligação bidirecional com um pai com modelo, use a seguinte instrução de associação em vez `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="f5cf4-118">[RelativeSource](relativesource-markupextension.md) é outra extensão de marcação que às vezes é usada em conjunto com ou em vez de `TemplateBinding` para executar Associação de propriedade relativa em um modelo.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="f5cf4-119">A descrição dos modelos de controle como um conceito não é abordada aqui; para obter mais informações, consulte [Control Styles and templates](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f5cf4-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="f5cf4-120">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="f5cf4-121">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `TemplateBinding` é atribuído como o valor <xref:System.Windows.TemplateBindingExtension.Property%2A> da classe de extensão subjacente <xref:System.Windows.TemplateBindingExtension>.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="f5cf4-122">A sintaxe do elemento de objeto é possível, mas não é exibida pois não tem aplicativo realístico.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="f5cf4-123">`TemplateBinding` é usado para preencher os valores dos setters usando expressões avaliadas. Usar a sintaxe do elemento de objeto `TemplateBinding` para preencher a sintaxe do elemento de propriedade `<Setter.Property>` é desnecessariamente detalhado.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="f5cf4-124">`TemplateBinding` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.TemplateBindingExtension.Property%2A> como sendo o par propriedade=valor:</span><span class="sxs-lookup"><span data-stu-id="f5cf4-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="f5cf4-125">O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="f5cf4-126">Como `TemplateBinding` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="f5cf4-127">Na implementação do processador XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o tratamento para essa extensão de marcação é definido pela classe <xref:System.Windows.TemplateBindingExtension>.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="f5cf4-128">`TemplateBinding` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="f5cf4-129">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f5cf4-130">Todas as extensões de marcação em XAML usam os caracteres `{` e `}` na sintaxe de atributo, que é a convenção pela qual o processador XAML reconhece que uma extensão de marcação precisa processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="f5cf4-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="f5cf4-131">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f5cf4-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cf4-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5cf4-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f5cf4-133">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f5cf4-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="f5cf4-134">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f5cf4-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="f5cf4-135">Extensões de marcação e XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="f5cf4-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="f5cf4-136">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="f5cf4-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="f5cf4-137">Extensão de marcação de associação</span><span class="sxs-lookup"><span data-stu-id="f5cf4-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
