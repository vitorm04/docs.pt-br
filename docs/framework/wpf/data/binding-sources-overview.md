---
title: "Visão geral das fontes de associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88f1a22fc15e85e687c7b7eeb0a6e01445277d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="binding-sources-overview"></a>Visão geral das fontes de associação
Na associação de dados, o objeto de origem da associação refere-se ao objeto do qual você obtém dados. Este tópico discute os tipos de objetos que você pode usar como a origem da associação.  
  
  
  
<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Tipos de origem da associação  
 A associação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dá suporte aos seguintes tipos de origem da associação:  
  
|Origem da associação|Descrição|  
|--------------------|-----------------|  
|Objetos [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]|Você pode associar a propriedades públicas, subpropriedades, bem como a indexadores de qualquer objeto [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]. O mecanismo de associação usa a reflexão do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] para obter os valores das propriedades. Como alternativa, os objetos que implementam <xref:System.ComponentModel.ICustomTypeDescriptor> ou tem um registrado <xref:System.ComponentModel.TypeDescriptionProvider> também funcionam com o mecanismo de associação.<br /><br /> Para obter mais informações sobre como implementar uma classe que pode servir como uma origem da associação, consulte [Implementando uma classe para a origem da associação](#classes) mais adiante neste tópico.|  
|objetos dinâmicos|Você pode vincular a propriedades disponíveis e indexadores de um objeto que implementa o <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Se você pode acessar o membro no código, pode associar a ele. Por exemplo, se um objeto dinâmico permite que você acesse um membro no código por meio de `someObjet.AProperty`, você pode associar a ele, definindo o caminho de associação como `AProperty`.|  
|Objetos [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)]|Você pode vincular a [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] objetos, como <xref:System.Data.DataTable>. O [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> implementa o <xref:System.ComponentModel.IBindingList> interface, que oferece notificações de alteração que o mecanismo de associação ouve.|  
|Objetos [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]|Você pode associar e executar `XPath` consultas em um <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>, ou <xref:System.Xml.XmlElement>. Uma maneira conveniente de acessar [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados que são a fonte de associação em marcação são usar um <xref:System.Windows.Data.XmlDataProvider> objeto. Para obter mais informações, consulte [Associar a dados XML usando um XMLDataProvider e consultas XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Você também pode associar a um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>, ou ligar os resultados de consultas executadas em objetos desses tipos usando LINQ para XML. Uma maneira conveniente usar o LINQ to XML para acessar dados XML que são a fonte de associação em marcação é usar um <xref:System.Windows.Data.ObjectDataProvider> objeto. Para obter mais informações, consulte [Associar a XDocument, XElement ou LINQ para resultados de Consulta XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|Objetos <xref:System.Windows.DependencyObject>|Você pode vincular a dependência propertiesof que qualquer <xref:System.Windows.DependencyObject>. Para obter um exemplo, consulte [Associar as propriedades de dois controles](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Implementando uma classe para a origem da associação  
 Você pode criar suas próprias origens da associação. Esta seção aborda as coisas que você precisa saber caso esteja implementando uma classe para servir como uma origem da associação.  
  
### <a name="providing-change-notifications"></a>Fornecendo notificações de alteração  
 Se você estiver usando uma <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> associação (porque deseja que seu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para atualizar as propriedades da fonte de associação dinamicamente quando alteração), você deve implementar um mecanismo de notificação de alteração de propriedade adequado. O mecanismo recomendado é o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ou classe dinâmica para implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface. Para obter mais informações, consulte [Implementar notificação de alteração da propriedade](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Se você criar um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto não implementa <xref:System.ComponentModel.INotifyPropertyChanged>, em seguida, você deve organizar seu próprio sistema de notificação certificar-se de que os dados usados em uma associação permanecem atuais. Você pode fornecer notificações de alteração, oferecendo suporte ao padrão `PropertyChanged` para cada propriedade que você deseja receber notificações de alteração. Para dar suporte a esse padrão, você define um evento *PropertyName*Changed para cada propriedade, em que *PropertyName* é o nome da propriedade. Você aciona o evento sempre que a propriedade é alterada.  
  
 Se a sua origem da associação implementa um desses mecanismos de notificação, as atualizações de destino ocorrem automaticamente. Se por alguma razão sua fonte de associação não fornece a propriedade adequada alterado notificações, você tem a opção de usar o <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> para atualizar a propriedade de destino explicitamente.  
  
### <a name="other-characteristics"></a>Outras características  
 A lista a seguir fornece outros pontos importantes a serem observados:  
  
-   Se você deseja criar o objeto no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a classe deve ter um construtor padrão. Em algumas linguagens [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)], como a [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], o construtor padrão pode ser criado para você.  
  
-   As propriedades que você usa como propriedades de origem da associação para uma associação devem ser propriedades públicas da sua classe. As propriedades de interface definidas explicitamente não podem ser acessadas para fins de associação, nem podem ser propriedades protegidas, particulares, internas ou virtuais que não têm implementação de base.  
  
-   Não é possível associar a campos públicos.  
  
-   O tipo da propriedade declarado na sua classe é o tipo que é passado para a associação. No entanto, o tipo usado pela associação depende, em última análise, do tipo da propriedade de destino da associação e não da propriedade da origem da associação. Caso haja uma diferença de tipo, talvez você queira escrever um conversor para manipular como a propriedade personalizada será inicialmente passada para a associação. Para obter mais informações, consulte <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Usando objetos inteiros como uma origem da associação  
 Você pode usar um objeto inteiro como uma origem da associação. Você pode especificar uma origem de associação usando o <xref:System.Windows.Data.Binding.Source%2A> ou <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade e, em seguida, forneça uma declaração de associação em branco: `{Binding}`. Os cenários em que isso é útil incluem a associação a objetos que são do tipo cadeia de caracteres, associação a objetos com várias propriedades nas quais você está interessado ou associação a objetos de coleção. Para obter um exemplo de associação a um objeto de coleção inteira, consulte [Usar o padrão de detalhes mestre com os dados hierárquicos](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Observe que talvez seja necessário aplicar uma lógica personalizada para que os dados sejam significativos para a propriedade de destino associada. A lógica personalizada pode ser na forma de um conversor personalizado (se o conversor de tipos padrão não existir) ou um <xref:System.Windows.DataTemplate>. Para obter mais informações sobre conversores, consulte a seção Conversão de dados da [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md). Para obter mais informações sobre modelos de dados, consulte [Visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Usando objetos de coleção como uma origem da associação  
 Frequentemente, o objeto que você deseja usar como a origem da associação é uma coleção de objetos personalizados. Cada objeto serve como a fonte para uma instância de uma associação repetida. Por exemplo, você pode ter uma coleção `CustomerOrders` que consiste em objetos `CustomerOrder`, em que o aplicativo itera na coleção para determinar quantos pedidos existem e os dados contidos em cada um.  
  
 Você pode enumerar sobre qualquer coleção que implementa o <xref:System.Collections.IEnumerable> interface. No entanto, para definir associações dinâmicas para que as inserções ou exclusões na coleção de atualizem o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticamente, a coleção deve implementar a <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Essa interface expõe um evento que deve ser acionado sempre que a coleção subjacente é alterada.  
  
 O <xref:System.Collections.ObjectModel.ObservableCollection%601> classe é uma implementação interna de uma coleção de dados que expõe o <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Os objetos de dados individuais dentro da coleção devem satisfazer aos requisitos descritos nas seções anteriores. Para obter um exemplo, consulte [Criar e associar a uma ObservableCollection](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md). Antes de implementar sua própria coleção, considere o uso de <xref:System.Collections.ObjectModel.ObservableCollection%601> ou uma coleção existente, como classes <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, e <xref:System.ComponentModel.BindingList%601>, entre outros.  
  
 O WPF nunca se associa diretamente a uma coleção. Se você especificar uma coleção como uma origem da associação, o WPF, na verdade, associará ao modo de exibição padrão da coleção. Para obter informações sobre os modos de exibição padrão, consulte [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Se você tiver um cenário avançado e você deseja implementar sua própria coleção, considere usar o <xref:System.Collections.IList> interface. <xref:System.Collections.IList>Fornece uma coleção não genérica de objetos que podem ser acessados separadamente por índice, o que pode melhorar o desempenho.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Requisitos de permissão na associação de dados  
 Ao associar dados, você deve considerar o nível de confiança do aplicativo. A tabela a seguir resume a quais tipos de propriedades é possível vincular-se, em um aplicativo que está sendo executado em confiança parcial ou confiança total:  
  
|Tipo de propriedade<br /><br /> (todos os modificadores de acesso)|Propriedade de objeto dinâmico|Propriedade de objeto dinâmico|Propriedade do CLR|Propriedade do CLR|Propriedade de dependência|Propriedade de dependência|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Nível de confiança**|**Confiança total**|**Confiança parcial**|**Confiança total**|**Confiança parcial**|**Confiança total**|**Confiança parcial**|  
|Classe pública|Sim|Sim|Sim|Sim|Sim|Sim|  
|Classe não pública|Sim|Não|Sim|Não|Sim|Sim|  
  
 Essa tabela descreve os seguintes pontos importantes sobre requisitos de permissão na associação de dados:  
  
-   Para propriedades do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], a associação de dados funciona enquanto o mecanismo de associação é capaz de acessar a propriedade da origem da associação usando reflexão. Caso contrário, o mecanismo de associação emitirá um aviso de que a propriedade não pôde ser encontrada e usará o valor de fallback ou o valor padrão, se estiver disponível.  
  
-   Você pode associar a propriedades em objetos dinâmicos que são definidos em tempo de execução ou tempo de compilação.  
  
-   Você sempre pode associar a propriedades de dependência.  
  
 O requisito de permissão para a associação [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] é semelhante. Em uma área restrita de confiança parcial, <xref:System.Windows.Data.XmlDataProvider> falha quando não tem permissões para acessar os dados especificados.  
  
 Objetos com um tipo anônimo são internos. Você pode associar a propriedades de tipos anônimos somente durante a execução em confiança total. Para obter mais informações sobre tipos anônimos, consulte [Tipos anônimos (Guia de programação em C#)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) ou [Tipos anônimos (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Para obter mais informações sobre a segurança de confiança parcial, consulte [Segurança de confiança parcial do WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.ObjectDataProvider>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Especificar a origem da associação](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Visão geral da vinculação de dados do WPF com LINQ to XML](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
