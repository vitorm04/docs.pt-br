---
title: 'Otimizando o desempenho: Associação de dados'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 25c0906e9f23948476732b10b2c5fb10fe4eb55f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401457"
---
# <a name="optimizing-performance-data-binding"></a>Otimizando o desempenho: Associação de dados
A vinculação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece aos aplicativos uma maneira simples e consistente para apresentar e interagir com os dados. Os elementos podem ser associados a dados de uma variedade de fontes de dados na forma de objetos CLR [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]e.  
  
 Este tópico apresenta recomendações de desempenho de vinculação de dados.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Como as referências de vinculação de dados são resolvidas  
 Antes de discutir os problemas de desempenho da vinculação de dados, vale a pena explorar como o mecanismo de vinculação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] resolve referências de objeto para associação.  
  
 A origem de uma [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Associação de dados pode ser qualquer objeto CLR. Você pode associar a propriedades, subpropriedades ou indexadores de um objeto CLR. As referências de associação são resolvidas usando a reflexão do Microsoft .NET Framework <xref:System.ComponentModel.ICustomTypeDescriptor>ou um. Aqui estão três métodos para resolver referências de objeto para associação.  
  
 O primeiro método envolve o uso de reflexão. Nesse caso, o <xref:System.Reflection.PropertyInfo> objeto é usado para descobrir os atributos da propriedade e fornece acesso aos metadados de propriedade. Ao usar a <xref:System.ComponentModel.ICustomTypeDescriptor> interface, o mecanismo de vinculação de dados usa essa interface para acessar os valores de propriedade. A <xref:System.ComponentModel.ICustomTypeDescriptor> interface é especialmente útil em casos em que o objeto não tem um conjunto estático de propriedades.  
  
 As notificações de alteração de propriedade podem ser fornecidas implementando a <xref:System.ComponentModel.INotifyPropertyChanged> interface ou usando as notificações de alteração associadas <xref:System.ComponentModel.TypeDescriptor>ao. No entanto, a estratégia preferida para implementar notificações de alteração de <xref:System.ComponentModel.INotifyPropertyChanged>propriedade é usar o.  
  
 Se o objeto de origem for um objeto CLR e a propriedade Source for uma propriedade CLR, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] o mecanismo de vinculação de dados precisará primeiro usar Reflection no objeto de origem <xref:System.ComponentModel.TypeDescriptor>para obter o e, em <xref:System.ComponentModel.PropertyDescriptor>seguida, consultar um. Essa sequência de operações de reflexão é potencialmente muito demorada de uma perspectiva de desempenho.  
  
 O segundo método para resolver referências de objeto envolve um objeto de origem CLR que implementa <xref:System.ComponentModel.INotifyPropertyChanged> a interface e uma propriedade Source que é uma propriedade CLR. Nesse caso, o mecanismo de vinculação de dados usa reflexão diretamente no tipo de fonte e obtém a propriedade necessária. Este ainda não é o melhor método, mas ele custará menos nos requisitos de conjunto de trabalho do que o primeiro método.  
  
 O terceiro método para resolver referências de objeto envolve um objeto de origem que é <xref:System.Windows.DependencyObject> um e uma propriedade de origem que <xref:System.Windows.DependencyProperty>é um. Nesse caso, o mecanismo de vinculação de dados não precisa usar reflexão. Em vez disso, o mecanismo de propriedade e o mecanismo de vinculação de dados resolvem juntos a referência da propriedade independentemente. Esse é o melhor método para resolver referências de objeto usadas para vinculação de dados.  
  
 A tabela a seguir compara a velocidade de vinculação de <xref:System.Windows.Controls.TextBlock.Text%2A> dados com a <xref:System.Windows.Controls.TextBlock> propriedade dos elementos 1000 usando esses três métodos.  
  
|**Associando a propriedade Text de um TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para uma propriedade de um objeto CLR|115|314|  
|Para uma propriedade de um objeto CLR que implementa<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Para um <xref:System.Windows.DependencyProperty> de um <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Associando a objetos CLR grandes  
 Há um impacto significativo no desempenho quando você vincula dados a um único objeto CLR com milhares de propriedades. Você pode minimizar esse impacto dividindo o objeto único em vários objetos CLR com menos Propriedades. A tabela mostra os tempos de associação e de renderização para vinculação de dados a um único objeto CLR grande versus vários objetos menores.  
  
|**Vinculação de dados de mil objetos TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para um objeto CLR com propriedades 1000|950|1200|  
|A 1000 objetos CLR com uma propriedade|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Associando a um ItemsSource  
 Considere um cenário no qual você tenha um objeto <xref:System.Collections.Generic.List%601> CLR que contém uma lista de funcionários que você deseja exibir em um. <xref:System.Windows.Controls.ListBox> Para criar uma correspondência entre esses dois objetos, você associaria sua lista <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>de funcionários à propriedade do. No entanto, suponha que você tenha um novo funcionário ingressando em seu grupo. Talvez você ache que, para inserir essa nova pessoa em seus valores associados <xref:System.Windows.Controls.ListBox> , bastaria adicionar essa pessoa à sua lista de funcionários e esperar que essa alteração fosse reconhecida pelo mecanismo de vinculação de dados automaticamente. Essa suposição provaria falso; na realidade, a alteração não será refletida <xref:System.Windows.Controls.ListBox> automaticamente. Isso ocorre porque o objeto <xref:System.Collections.Generic.List%601> CLR não gera automaticamente um evento de alteração de coleção. Para obter <xref:System.Windows.Controls.ListBox> as alterações, você precisaria recriar sua lista de funcionários e anexá-la novamente <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> à propriedade do <xref:System.Windows.Controls.ListBox>... Embora essa solução funcione, ela ocasiona um grande impacto no desempenho. Sempre que você reatribui o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.ListBox> para um novo objeto, o <xref:System.Windows.Controls.ListBox> primeiro joga seus itens anteriores e gera novamente sua lista inteira. O impacto no desempenho será ampliado se <xref:System.Windows.Controls.ListBox> seus mapas forem complexos <xref:System.Windows.DataTemplate>.  
  
 Uma solução muito eficiente para esse problema é tornar sua lista de funcionários um <xref:System.Collections.ObjectModel.ObservableCollection%601>. Um <xref:System.Collections.ObjectModel.ObservableCollection%601> objeto gera uma notificação de alteração que o mecanismo de vinculação de dados pode receber. O evento adiciona ou remove um item de um <xref:System.Windows.Controls.ItemsControl> sem a necessidade de regenerar a lista inteira.  
  
 A tabela a seguir mostra o tempo necessário para atualizar o <xref:System.Windows.Controls.ListBox> (com a virtualização de interface do usuário desativada) quando um item é adicionado. O número na primeira linha representa o tempo decorrido quando o objeto CLR <xref:System.Collections.Generic.List%601> está associado a <xref:System.Windows.Controls.ListBox> um <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>elemento. O número na segunda linha representa o tempo decorrido quando um <xref:System.Collections.ObjectModel.ObservableCollection%601> está associado <xref:System.Windows.Controls.ListBox> ao elemento <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Observe a economia de tempo significativa usando <xref:System.Collections.ObjectModel.ObservableCollection%601> a estratégia de vinculação de dados.  
  
|**Vinculação de dados de ItemsSource**|**Atualizar tempo para 1 item (ms)**|  
|--------------------------------------|---------------------------------------|  
|Para um objeto <xref:System.Collections.Generic.List%601> CLR|1656|  
|Para um<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Associar IList a ItemsControl não IEnumerable  
 Se você tiver uma opção entre ligar um <xref:System.Collections.Generic.IList%601> ou um <xref:System.Collections.IEnumerable> <xref:System.Windows.Controls.ItemsControl> objeto, escolha o <xref:System.Collections.Generic.IList%601> objeto. Associação <xref:System.Collections.IEnumerable> a uma <xref:System.Windows.Controls.ItemsControl> força [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para criar um objeto <xref:System.Collections.Generic.IList%601> wrapper, o que significa que o desempenho é afetado pela sobrecarga desnecessária de um segundo objeto.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Não converta objetos CLR em XML apenas para vinculação de dados.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]permite associar dados ao [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] conteúdo; no entanto, a vinculação de dados ao [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] conteúdo é mais lenta do que a vinculação de dados com objetos CLR. Não converta os dados do objeto CLR em XML se a única finalidade for a associação de dados.  
  
## <a name="see-also"></a>Consulte também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Passo a passo: Armazenando em cache dados de aplicativo em um aplicativo WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
