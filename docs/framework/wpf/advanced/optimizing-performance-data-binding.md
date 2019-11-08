---
title: 'Otimizando desempenho: vinculação de dados'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 9b302be3ed9f01ccd27470063f49966dc7d74708
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740802"
---
# <a name="optimizing-performance-data-binding"></a>Otimizando desempenho: vinculação de dados
A vinculação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece aos aplicativos uma maneira simples e consistente para apresentar e interagir com os dados. Os elementos podem ser associados a dados de uma variedade de fontes de dados na forma de objetos CLR e XML.  
  
 Este tópico apresenta recomendações de desempenho de vinculação de dados.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Como as referências de vinculação de dados são resolvidas  
 Antes de discutir os problemas de desempenho da vinculação de dados, vale a pena explorar como o mecanismo de vinculação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] resolve referências de objeto para associação.  
  
 A origem de uma associação de dados de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode ser qualquer objeto CLR. Você pode associar a propriedades, subpropriedades ou indexadores de um objeto CLR. As referências de associação são resolvidas usando a reflexão Microsoft .NET estrutura ou uma <xref:System.ComponentModel.ICustomTypeDescriptor>. Aqui estão três métodos para resolver referências de objeto para associação.  
  
 O primeiro método envolve o uso de reflexão. Nesse caso, o objeto <xref:System.Reflection.PropertyInfo> é usado para descobrir os atributos da propriedade e fornece acesso aos metadados de propriedade. Ao usar a interface <xref:System.ComponentModel.ICustomTypeDescriptor>, o mecanismo de vinculação de dados usa essa interface para acessar os valores de propriedade. A interface <xref:System.ComponentModel.ICustomTypeDescriptor> é especialmente útil em casos em que o objeto não tem um conjunto estático de propriedades.  
  
 As notificações de alteração de propriedade podem ser fornecidas implementando a interface <xref:System.ComponentModel.INotifyPropertyChanged> ou usando as notificações de alteração associadas ao <xref:System.ComponentModel.TypeDescriptor>. No entanto, a estratégia preferida para implementar notificações de alteração de propriedade é usar <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Se o objeto de origem for um objeto CLR e a propriedade Source for uma propriedade CLR, o mecanismo de associação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] precisará primeiro usar reflexão no objeto de origem para obter o <xref:System.ComponentModel.TypeDescriptor>e, em seguida, consultar uma <xref:System.ComponentModel.PropertyDescriptor>. Essa sequência de operações de reflexão é potencialmente muito demorada de uma perspectiva de desempenho.  
  
 O segundo método para resolver referências de objeto envolve um objeto de origem CLR que implementa a interface <xref:System.ComponentModel.INotifyPropertyChanged> e uma propriedade Source que é uma propriedade CLR. Nesse caso, o mecanismo de vinculação de dados usa reflexão diretamente no tipo de fonte e obtém a propriedade necessária. Este ainda não é o melhor método, mas ele custará menos nos requisitos de conjunto de trabalho do que o primeiro método.  
  
 O terceiro método para resolver referências de objeto envolve um objeto de origem que é um <xref:System.Windows.DependencyObject> e uma propriedade de origem que é um <xref:System.Windows.DependencyProperty>. Nesse caso, o mecanismo de vinculação de dados não precisa usar reflexão. Em vez disso, o mecanismo de propriedade e o mecanismo de vinculação de dados resolvem juntos a referência da propriedade independentemente. Esse é o melhor método para resolver referências de objeto usadas para vinculação de dados.  
  
 A tabela a seguir compara a velocidade de vinculação de dados com a propriedade <xref:System.Windows.Controls.TextBlock.Text%2A> de 1000 <xref:System.Windows.Controls.TextBlock> elementos usando esses três métodos.  
  
|**Associando a propriedade Text de um TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para uma propriedade de um objeto CLR|115|314|  
|Para uma propriedade de um objeto CLR que implementa <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Para uma <xref:System.Windows.DependencyProperty> de um <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Associando a objetos CLR grandes  
 Há um impacto significativo no desempenho quando você vincula dados a um único objeto CLR com milhares de propriedades. Você pode minimizar esse impacto dividindo o objeto único em vários objetos CLR com menos Propriedades. A tabela mostra os tempos de associação e de renderização para vinculação de dados a um único objeto CLR grande versus vários objetos menores.  
  
|**Vinculação de dados de mil objetos TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para um objeto CLR com propriedades 1000|950|1200|  
|A 1000 objetos CLR com uma propriedade|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Associando a um ItemsSource  
 Considere um cenário no qual você tenha um objeto CLR <xref:System.Collections.Generic.List%601> que contém uma lista de funcionários que você deseja exibir em um <xref:System.Windows.Controls.ListBox>. Para criar uma correspondência entre esses dois objetos, você associaria sua lista de funcionários à propriedade <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> da <xref:System.Windows.Controls.ListBox>. No entanto, suponha que você tenha um novo funcionário ingressando em seu grupo. Talvez você ache que, para inserir essa nova pessoa em seus valores <xref:System.Windows.Controls.ListBox> associados, bastaria adicionar essa pessoa à sua lista de funcionários e esperar que essa alteração fosse reconhecida pelo mecanismo de vinculação de dados automaticamente. Essa suposição provaria falso; na realidade, a alteração não será refletida na <xref:System.Windows.Controls.ListBox> automaticamente. Isso ocorre porque o objeto CLR <xref:System.Collections.Generic.List%601> não gera automaticamente um evento de alteração de coleção. Para obter as <xref:System.Windows.Controls.ListBox> para obter as alterações, você precisaria recriar sua lista de funcionários e anexá-la novamente à propriedade <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> da <xref:System.Windows.Controls.ListBox>. Embora essa solução funcione, ela ocasiona um grande impacto no desempenho. Sempre que você reatribui o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.ListBox> a um novo objeto, a <xref:System.Windows.Controls.ListBox> primeiro lança seus itens anteriores e gera novamente sua lista inteira. O impacto no desempenho será ampliado se o <xref:System.Windows.Controls.ListBox> for mapeado para um <xref:System.Windows.DataTemplate>complexo.  
  
 Uma solução muito eficiente para esse problema é tornar sua lista de funcionários um <xref:System.Collections.ObjectModel.ObservableCollection%601>. Um objeto <xref:System.Collections.ObjectModel.ObservableCollection%601> gera uma notificação de alteração que o mecanismo de vinculação de dados pode receber. O evento adiciona ou remove um item de um <xref:System.Windows.Controls.ItemsControl> sem a necessidade de regenerar a lista inteira.  
  
 A tabela a seguir mostra o tempo necessário para atualizar o <xref:System.Windows.Controls.ListBox> (com a virtualização de interface do usuário desativada) quando um item é adicionado. O número na primeira linha representa o tempo decorrido quando o objeto CLR <xref:System.Collections.Generic.List%601> está associado à <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>de <xref:System.Windows.Controls.ListBox> elemento. O número na segunda linha representa o tempo decorrido quando um <xref:System.Collections.ObjectModel.ObservableCollection%601> está associado à <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>do elemento de <xref:System.Windows.Controls.ListBox>. Observe a economia de tempo significativa usando a estratégia de associação de dados <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
|**Vinculação de dados de ItemsSource**|**Atualizar tempo para 1 item (ms)**|  
|--------------------------------------|---------------------------------------|  
|Para um objeto CLR <xref:System.Collections.Generic.List%601>|1656|  
|Para um <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Associar IList a ItemsControl não IEnumerable  
 Se você tiver uma opção entre associar um <xref:System.Collections.Generic.IList%601> ou um <xref:System.Collections.IEnumerable> a um objeto <xref:System.Windows.Controls.ItemsControl>, escolha o objeto <xref:System.Collections.Generic.IList%601>. A associação de <xref:System.Collections.IEnumerable> a uma <xref:System.Windows.Controls.ItemsControl> força o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a criar um objeto de <xref:System.Collections.Generic.IList%601> de invólucro, o que significa que o desempenho é afetado pela sobrecarga desnecessária de um segundo objeto.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Não converta objetos CLR em XML apenas para vinculação de dados.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que você associe dados ao conteúdo XML; no entanto, a vinculação de dados ao conteúdo XML é mais lenta do que a vinculação de dados com objetos CLR. Não converta os dados do objeto CLR em XML se a única finalidade for a associação de dados.  
  
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
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
