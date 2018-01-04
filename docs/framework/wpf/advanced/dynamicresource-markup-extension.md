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
# <a name="dynamicresource-markup-extension"></a>Extensão de marcação DynamicResource
Fornece um valor para qualquer atributo da propriedade [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adiando esse valor para ser uma referência para um recurso definido. O comportamento de pesquisa desse recurso é análogo à pesquisa em tempo de execução.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Uso do elemento propriedade XAML  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`key`|A chave para o recurso solicitado. Essa chave foi inicialmente atribuída pelo [diretiva X:Key](../../../../docs/framework/xaml-services/x-key-directive.md) se um recurso foi criado na marcação ou foi fornecido como o `key` parâmetro ao chamar <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> se o recurso foi criado em código.|  
  
## <a name="remarks"></a>Comentários  
 Um `DynamicResource` criará uma expressão temporária durante a compilação inicial e, portanto, adiará a pesquisa por recursos até que o valor de recurso solicitado seja realmente necessário para construir um objeto. Isso pode ocorrer após o carregamento da página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. O valor do recurso será encontrado com base na pesquisa pela chave em todos os dicionários de recursos ativos, no escopo da página atual, e substituirá a expressão de espaço reservado da compilação.  
  
> [!IMPORTANT]
>  Em termos de precedência de propriedade de dependência, uma expressão `DynamicResource` é equivalente à posição em que a referência de recurso dinâmico é aplicada. Se um valor local for definido para uma propriedade que tinha uma expressão `DynamicResource` como valor local anteriormente, o `DynamicResource` será totalmente removido. Para obter mais detalhes, consulte [Precedência do valor da propriedade da dependência](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Determinados cenários de acesso a recursos são particularmente apropriados para `DynamicResource`, ao contrário de uma [Extensão de Marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) para ver uma discussão sobre os méritos relativos e as implicações de desempenho de `DynamicResource` e `StaticResource`.  
  
 Especificado <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> devem corresponder a um recurso existente determinado pelo [diretiva X:Key](../../../../docs/framework/xaml-services/x-key-directive.md) em algum nível na sua página, aplicativo, os temas de controle disponíveis e recursos externos ou recursos do sistema e o recurso de pesquisa ocorrerá nessa ordem. Para obter mais informações sobre a pesquisa de recursos para recursos estáticos e dinâmicos, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Uma chave de recurso pode ser qualquer cadeia de caracteres definida na [Gramática XamlName](../../../../docs/framework/xaml-services/xamlname-grammar.md). Uma chave de recurso também pode ser outros tipos de objeto, como um <xref:System.Type>. Um <xref:System.Type> chave é fundamental para como os controles podem ser estilizados por temas. Para obter mais informações, consulte [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]para a pesquisa de valores de recursos, tais como <xref:System.Windows.FrameworkElement.FindResource%2A>, seguem a mesma lógica de pesquisa de recursos usada por `DynamicResource`.  
  
 O meio declarativo alternativo de referenciar um recurso é como uma [Extensão de Marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `DynamicResource` é atribuído como o valor <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> da classe de extensão subjacente <xref:System.Windows.DynamicResourceExtension>.  
  
 `DynamicResource` pode ser usado na sintaxe de elemento de objeto. Nesse caso, especificando o valor de <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> propriedade é necessária.  
  
 `DynamicResource` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> como sendo o par propriedade=valor:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais. Como `DynamicResource` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.  
  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação do processador, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.DynamicResourceExtension> classe.  
  
 `DynamicResource` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também  
 [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Recursos e código](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Diretiva x:Key](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
