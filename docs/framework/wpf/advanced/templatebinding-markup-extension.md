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
ms.openlocfilehash: 6d89978b907c8f124b5162c97de5edc034cf1e95
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976666"
---
# <a name="templatebinding-markup-extension"></a>Extensão de marcação TemplateBinding
Vincula o valor de uma propriedade em um modelo de controle para ser o valor de outra propriedade no controle personalizado.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>Uso do Atributo XAML (para propriedade Setter em um modelo ou estilo)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> da propriedade sendo definida na sintaxe setter.|  
|`sourceProperty`|Outra propriedade de dependência que existe no tipo que está sendo personalizado, especificada por <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - ou -<br /><br /> Um nome de propriedade "pontilhado" definido por um tipo diferente do tipo de destino sendo personalizado. Isso é, na verdade, um <xref:System.Windows.PropertyPath>. Consulte [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Comentários  
 Uma `TemplateBinding` é uma forma otimizada de uma [Associação](binding-markup-extension.md) para cenários de modelo, análoga a um `Binding` construído com `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`. Um `TemplateBinding` é sempre uma associação unidirecional, mesmo se as propriedades envolverem associação bidirecional padrão. Ambas as propriedades envolvidas devem ser propriedades de dependência. Para obter uma ligação bidirecional com um pai com modelo, use a seguinte instrução de associação em vez `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`. 
  
 [RelativeSource](relativesource-markupextension.md) é outra extensão de marcação que às vezes é usada em conjunto com ou em vez de `TemplateBinding` para executar Associação de propriedade relativa em um modelo.  
  
 A descrição dos modelos de controle como um conceito não é abordada aqui; para obter mais informações, consulte [Control Styles and templates](../controls/control-styles-and-templates.md).  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `TemplateBinding` é atribuído como o valor <xref:System.Windows.TemplateBindingExtension.Property%2A> da classe de extensão subjacente <xref:System.Windows.TemplateBindingExtension>.  
  
 A sintaxe do elemento de objeto é possível, mas não é exibida pois não tem aplicativo realístico. `TemplateBinding` é usado para preencher os valores dos setters usando expressões avaliadas. Usar a sintaxe do elemento de objeto `TemplateBinding` para preencher a sintaxe do elemento de propriedade `<Setter.Property>` é desnecessariamente detalhado.  
  
 `TemplateBinding` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.TemplateBindingExtension.Property%2A> como sendo o par propriedade=valor:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais. Como `TemplateBinding` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.  
  
 Na implementação do processador XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o tratamento para essa extensão de marcação é definido pela classe <xref:System.Windows.TemplateBindingExtension>.  
  
 `TemplateBinding` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. Todas as extensões de marcação em XAML usam os caracteres `{` e `}` na sintaxe de atributo, que é a convenção pela qual o processador XAML reconhece que uma extensão de marcação precisa processar o atributo. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilo e modelagem](../controls/styling-and-templating.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md)
- [RelativeSource MarkupExtension](relativesource-markupextension.md)
- [Extensão de marcação de associação](binding-markup-extension.md)
