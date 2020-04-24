---
title: Extensão de marcação StaticResource
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646207"
---
# <a name="staticresource-markup-extension"></a>Extensão de marcação StaticResource
Fornece um valor para qualquer atributo de propriedade [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pesquisando uma referência a um recurso já definido. O comportamento de pesquisa para esse recurso é análogo à pesquisa de tempo de carga, que procurará os recursos que foram previamente carregados da marcação da página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atual, bem como outras fontes de aplicativo, e gerará esse valor de recurso como o valor da propriedade nos objetos de tempo de execução.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`key`|A chave para o recurso solicitado. Esta chave foi inicialmente atribuída pela [Diretiva x:Chave](../../../desktop-wpf/xaml-services/xkey-directive.md) se um recurso foi criado `key` na marcação ou foi fornecido como parâmetro ao ligar <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> se o recurso foi criado em código.|  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
> Um `StaticResource` não deve tentar fazer uma referência direta a um recurso que está definido lexicalmente mais à frente no arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. A tentativa de fazê-lo não é suportada e, mesmo que tal referência não falhe, tentar a referência de <xref:System.Windows.ResourceDictionary> encaminhamento incorrerá em uma penalidade de desempenho de tempo de carga quando as tabelas de hash internas representando a são pesquisadas. Para obter melhores resultados, ajuste a composição de seus dicionários de recursos de forma a evitar referências adiante. Se você não puder evitar uma referência à frente, use [Extensão de marcação DynamicResource](dynamicresource-markup-extension.md).  
  
 O especificado <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> deve corresponder a um recurso existente, identificado com uma [diretiva x:Chave](../../../desktop-wpf/xaml-services/xkey-directive.md) em algum nível em sua página, aplicativo, os temas de controle disponíveis e recursos externos ou recursos do sistema. A pesquisa de recursos ocorre nessa ordem. Para obter mais informações sobre o comportamento de pesquisa de recursos para recursos estáticos e dinâmicos, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Uma tecla de recurso pode ser qualquer cadeia de caracteres definida na [Gramática XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Uma chave de recurso também pode ser <xref:System.Type>de outros tipos de objetos, como a . Uma <xref:System.Type> chave é fundamental para como os controles podem ser estilizados por temas, através de uma chave de estilo implícita. Para obter mais informações, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).  
  
 O meio declarativo alternativo de referenciar um recurso é como uma [Extensão de Marcação DynamicResource](dynamicresource-markup-extension.md).  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `StaticResource` é atribuído como o valor <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> da classe de extensão subjacente <xref:System.Windows.StaticResourceExtension>.  
  
 O `StaticResource` pode ser usado na sintaxe de elemento de objeto. Neste caso, é necessário especificar o valor da <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> propriedade.  
  
 `StaticResource` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> como sendo o par propriedade=valor:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais. Como `StaticResource` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação do processador, o manuseio para esta <xref:System.Windows.StaticResourceExtension> extensão de marcação é definido pela classe.  
  
 `StaticResource` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Confira também

- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Recursos e código](resources-and-code.md)
