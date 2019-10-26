---
title: Visão geral das fontes de associação
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: cf5873cdf137573826d5361d077e0534e8cba1f0
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920282"
---
# <a name="binding-sources-overview"></a>Visão geral das fontes de associação
Na associação de dados, o objeto de origem da associação refere-se ao objeto do qual você obtém dados. Este tópico discute os tipos de objetos que você pode usar como a origem da associação.

<a name="binding_sources"></a>
## <a name="binding-source-types"></a>Tipos de origem da associação
 A associação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dá suporte aos seguintes tipos de origem da associação:

|Origem da associação|Descrição|
|--------------------|-----------------|
|objetos Common Language Runtime (CLR)|Você pode associar a propriedades públicas, subpropriedades, bem como indexadores, de qualquer objeto Common Language Runtime (CLR). O mecanismo de associação usa a reflexão do CLR para obter os valores das propriedades. Como alternativa, os objetos que implementam <xref:System.ComponentModel.ICustomTypeDescriptor> ou têm um <xref:System.ComponentModel.TypeDescriptionProvider> registrado também funcionam com o mecanismo de associação.<br /><br /> Para obter mais informações sobre como implementar uma classe que pode servir como uma origem da associação, consulte [Implementando uma classe para a origem da associação](#classes) mais adiante neste tópico.|
|objetos dinâmicos|Você pode associar a propriedades disponíveis e indexadores de um objeto que implementa a interface <xref:System.Dynamic.IDynamicMetaObjectProvider>. Se você pode acessar o membro no código, pode associar a ele. Por exemplo, se um objeto dinâmico permite que você acesse um membro no código por meio de `someObjet.AProperty`, você pode associar a ele, definindo o caminho de associação como `AProperty`.|
|Objetos ADO.NET|Você pode associar a objetos ADO.NET, como <xref:System.Data.DataTable>. O <xref:System.Data.DataView> ADO.NET implementa a interface <xref:System.ComponentModel.IBindingList>, que fornece notificações de alteração que o mecanismo de associação escuta.|
|Objetos [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]|Você pode associar e executar `XPath` consultas em um <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>ou <xref:System.Xml.XmlElement>. Uma maneira conveniente de acessar dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] que é a origem da associação na marcação é usar um objeto <xref:System.Windows.Data.XmlDataProvider>. Para obter mais informações, consulte [Associar a dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Você também pode associar a um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>ou associar os resultados de consultas executadas em objetos desses tipos usando LINQ to XML. Uma maneira conveniente de usar LINQ to XML para acessar dados XML que é a origem da associação na marcação é usar um objeto <xref:System.Windows.Data.ObjectDataProvider>. Para obter mais informações, consulte [Associar a XDocument, XElement ou LINQ para resultados de Consulta XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|
|Objetos <xref:System.Windows.DependencyObject>|Você pode associar a propriedades de dependência de qualquer <xref:System.Windows.DependencyObject>. Para obter um exemplo, consulte [Associar as propriedades de dois controles](how-to-bind-the-properties-of-two-controls.md).|

<a name="classes"></a>
## <a name="implementing-a-class-for-the-binding-source"></a>Implementando uma classe para a origem da associação
 Você pode criar suas próprias origens da associação. Esta seção aborda as coisas que você precisa saber caso esteja implementando uma classe para servir como uma origem da associação.

### <a name="providing-change-notifications"></a>Fornecendo notificações de alteração
 Se você estiver usando uma associação <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> (porque você deseja que seu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] seja atualizado quando as propriedades de origem da Associação forem alteradas dinamicamente), você deverá implementar um mecanismo de notificação de propriedade alterada adequado. O mecanismo recomendado é que o CLR ou a classe dinâmica implemente a interface <xref:System.ComponentModel.INotifyPropertyChanged>. Para obter mais informações, consulte [Implementar notificação de alteração da propriedade](how-to-implement-property-change-notification.md).

 Se você criar um objeto CLR que não implementa <xref:System.ComponentModel.INotifyPropertyChanged>, precisará organizar seu próprio sistema de notificação para certificar-se de que os dados usados em uma associação permaneçam atuais. Você pode fornecer notificações de alteração, oferecendo suporte ao padrão `PropertyChanged` para cada propriedade que você deseja receber notificações de alteração. Para dar suporte a esse padrão, você define um evento *PropertyName*Changed para cada propriedade, em que *PropertyName* é o nome da propriedade. Você aciona o evento sempre que a propriedade é alterada.

 Se a sua origem da associação implementa um desses mecanismos de notificação, as atualizações de destino ocorrem automaticamente. Se por algum motivo sua fonte de associação não fornecer as notificações de propriedade alteradas adequadas, você terá a opção de usar o método <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> para atualizar a propriedade de destino explicitamente.

### <a name="other-characteristics"></a>Outras características
 A lista a seguir fornece outros pontos importantes a serem observados:

- Se você quiser criar o objeto em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a classe deverá ter um construtor sem parâmetros. Em algumas linguagens .NET, como C#, o construtor sem parâmetros pode ser criado para você.

- As propriedades que você usa como propriedades de origem da associação para uma associação devem ser propriedades públicas da sua classe. As propriedades de interface definidas explicitamente não podem ser acessadas para fins de associação, nem podem ser propriedades protegidas, particulares, internas ou virtuais que não têm implementação de base.

- Não é possível associar a campos públicos.

- O tipo da propriedade declarado na sua classe é o tipo que é passado para a associação. No entanto, o tipo usado pela associação depende, em última análise, do tipo da propriedade de destino da associação e não da propriedade da origem da associação. Caso haja uma diferença de tipo, talvez você queira escrever um conversor para manipular como a propriedade personalizada será inicialmente passada para a associação. Para obter mais informações, consulte <xref:System.Windows.Data.IValueConverter>.

<a name="objects"></a>
## <a name="using-entire-objects-as-a-binding-source"></a>Usando objetos inteiros como uma origem da associação
 Você pode usar um objeto inteiro como uma origem da associação. Você pode especificar uma fonte de associação usando o <xref:System.Windows.Data.Binding.Source%2A> ou a propriedade <xref:System.Windows.FrameworkElement.DataContext%2A> e, em seguida, fornecer uma declaração de associação em branco: `{Binding}`. Os cenários em que isso é útil incluem a associação a objetos que são do tipo cadeia de caracteres, associação a objetos com várias propriedades nas quais você está interessado ou associação a objetos de coleção. Para obter um exemplo de associação a um objeto de coleção inteira, consulte [Usar o padrão de detalhes mestre com os dados hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

 Observe que talvez seja necessário aplicar uma lógica personalizada para que os dados sejam significativos para a propriedade de destino associada. A lógica personalizada pode estar na forma de um conversor personalizado (se a conversão de tipo padrão não existir) ou uma <xref:System.Windows.DataTemplate>. Para obter mais informações sobre conversores, consulte a seção Conversão de dados da [Visão geral de associação de dados](data-binding-overview.md). Para obter mais informações sobre modelos de dados, consulte [Visão geral de modelagem de dados](data-templating-overview.md).

<a name="collections"></a>
## <a name="using-collection-objects-as-a-binding-source"></a>Usando objetos de coleção como uma origem da associação
 Frequentemente, o objeto que você deseja usar como a origem da associação é uma coleção de objetos personalizados. Cada objeto serve como a fonte para uma instância de uma associação repetida. Por exemplo, você pode ter uma coleção `CustomerOrders` que consiste em objetos `CustomerOrder`, em que o aplicativo itera na coleção para determinar quantos pedidos existem e os dados contidos em cada um.

 Você pode enumerar em qualquer coleção que implemente a interface <xref:System.Collections.IEnumerable>. No entanto, para configurar associações dinâmicas para que as inserções ou exclusões na coleção atualizem o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticamente, a coleção deve implementar a interface <xref:System.Collections.Specialized.INotifyCollectionChanged>. Essa interface expõe um evento que deve ser acionado sempre que a coleção subjacente é alterada.

 A classe <xref:System.Collections.ObjectModel.ObservableCollection%601> é uma implementação interna de uma coleção de dados que expõe a interface <xref:System.Collections.Specialized.INotifyCollectionChanged>. Os objetos de dados individuais dentro da coleção devem satisfazer aos requisitos descritos nas seções anteriores. Para obter um exemplo, consulte [Criar e associar a uma ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md). Antes de implementar sua própria coleção, considere o uso de <xref:System.Collections.ObjectModel.ObservableCollection%601> ou uma das classes de coleção existentes, como <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>e <xref:System.ComponentModel.BindingList%601>, entre muitas outras.

 O WPF nunca se associa diretamente a uma coleção. Se você especificar uma coleção como uma origem da associação, o WPF, na verdade, associará ao modo de exibição padrão da coleção. Para obter informações sobre os modos de exibição padrão, consulte [Visão geral de associação de dados](data-binding-overview.md).

 Se você tiver um cenário avançado e desejar implementar sua própria coleção, considere usar a interface <xref:System.Collections.IList>. <xref:System.Collections.IList> fornece uma coleção não genérica de objetos que podem ser acessados individualmente por índice, o que pode melhorar o desempenho.

<a name="permissions"></a>
## <a name="permission-requirements-in-data-binding"></a>Requisitos de permissão na associação de dados
 Ao associar dados, você deve considerar o nível de confiança do aplicativo. A tabela a seguir resume a quais tipos de propriedades é possível vincular-se, em um aplicativo que está sendo executado em confiança parcial ou confiança total:

|Tipo de propriedade<br /><br /> (todos os modificadores de acesso)|Propriedade de objeto dinâmico|Propriedade de objeto dinâmico|Propriedade do CLR|Propriedade do CLR|Propriedade de dependência|Propriedade de dependência|
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|
|**Nível de confiança**|**Confiança total**|**Confiança parcial**|**Confiança total**|**Confiança parcial**|**Confiança total**|**Confiança parcial**|
|Classe pública|Sim|Sim|Sim|Sim|Sim|Sim|
|Classe não pública|Sim|Não|Sim|Não|Sim|Sim|

 Essa tabela descreve os seguintes pontos importantes sobre requisitos de permissão na associação de dados:

- Para propriedades CLR, a vinculação de dados funciona contanto que o mecanismo de associação seja capaz de acessar a propriedade de origem da Associação usando reflexão. Caso contrário, o mecanismo de associação emitirá um aviso de que a propriedade não pôde ser encontrada e usará o valor de fallback ou o valor padrão, se estiver disponível.

- Você pode associar a propriedades em objetos dinâmicos que são definidos em tempo de execução ou tempo de compilação.

- Você sempre pode associar a propriedades de dependência.

 O requisito de permissão para a associação [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] é semelhante. Em uma área restrita de confiança parcial, <xref:System.Windows.Data.XmlDataProvider> falha quando não tem permissões para acessar os dados especificados.

 Objetos com um tipo anônimo são internos. Você pode associar a propriedades de tipos anônimos somente durante a execução em confiança total. Para obter mais informações sobre tipos anônimos, consulte [Tipos anônimos (Guia de programação em C#)](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) ou [Tipos anônimos (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).

 Para obter mais informações sobre a segurança de confiança parcial, consulte [Segurança de confiança parcial do WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Especificar a origem da associação](how-to-specify-the-binding-source.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Visão geral da vinculação de dados do WPF com LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Otimizar o desempenho da Associação de dados](../advanced/optimizing-performance-data-binding.md)
