---
title: 'Otimizando desempenho: vinculação de dados'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: da870e9459ee2cbe0384c146546c378fb7247f03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548773"
---
# <a name="optimizing-performance-data-binding"></a>Otimizando desempenho: vinculação de dados
A vinculação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece aos aplicativos uma maneira simples e consistente para apresentar e interagir com os dados. Os elementos podem ser associados aos dados de uma variedade de fontes de dados na forma de objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] e [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Este tópico apresenta recomendações de desempenho de vinculação de dados.  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Como as referências de vinculação de dados são resolvidas  
 Antes de discutir os problemas de desempenho da vinculação de dados, vale a pena explorar como o mecanismo de vinculação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] resolve referências de objeto para associação.  
  
 A origem de uma vinculação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode ser qualquer objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Você pode associar a propriedades, subpropriedades ou indexadores de um objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. As referências de associação são resolvidas usando a reflexão do Microsoft .NET Framework ou um <xref:System.ComponentModel.ICustomTypeDescriptor>. Aqui estão três métodos para resolver referências de objeto para associação.  
  
 O primeiro método envolve o uso de reflexão. Nesse caso, o <xref:System.Reflection.PropertyInfo> objeto é usado para descobrir os atributos da propriedade e fornece acesso aos metadados de propriedade. Ao usar o <xref:System.ComponentModel.ICustomTypeDescriptor> interface, o mecanismo de associação de dados usa esta interface para acessar os valores de propriedade. O <xref:System.ComponentModel.ICustomTypeDescriptor> interface é especialmente útil em casos onde o objeto não tem um conjunto estático de propriedades.  
  
 As notificações de alteração de propriedade podem ser fornecidas implementando a <xref:System.ComponentModel.INotifyPropertyChanged> interface ou usando as notificações de alteração associadas a <xref:System.ComponentModel.TypeDescriptor>. No entanto, a estratégia preferencial para implementar notificações de alteração de propriedade é usar <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Se o objeto de origem for um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto e a propriedade de origem é um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriedade, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mecanismo de associação de dados deve primeiro usar reflexão no objeto de origem para obter o <xref:System.ComponentModel.TypeDescriptor>e, em seguida, consultar um <xref:System.ComponentModel.PropertyDescriptor>. Essa sequência de operações de reflexão é potencialmente muito demorada de uma perspectiva de desempenho.  
  
 O segundo método para resolver referências de objeto envolve um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto de origem que implementa o <xref:System.ComponentModel.INotifyPropertyChanged> interface e uma propriedade de fonte que é um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriedade. Nesse caso, o mecanismo de vinculação de dados usa reflexão diretamente no tipo de fonte e obtém a propriedade necessária. Este ainda não é o melhor método, mas ele custará menos nos requisitos de conjunto de trabalho do que o primeiro método.  
  
 O terceiro método para resolver referências de objeto envolve um objeto de fonte que é uma <xref:System.Windows.DependencyObject> e uma propriedade de fonte que é um <xref:System.Windows.DependencyProperty>. Nesse caso, o mecanismo de vinculação de dados não precisa usar reflexão. Em vez disso, o mecanismo de propriedade e o mecanismo de vinculação de dados resolvem juntos a referência da propriedade independentemente. Esse é o melhor método para resolver referências de objeto usadas para vinculação de dados.  
  
 A tabela abaixo compara a velocidade da associação de dados de <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade de mil <xref:System.Windows.Controls.TextBlock> elementos usando esses três métodos.  
  
|**Associando a propriedade Text de um TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para uma propriedade de um objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]|115|314|  
|Para uma propriedade de um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto que implementa <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Para uma <xref:System.Windows.DependencyProperty> de um <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Associando a objetos CLR grandes  
 Há um impacto significativo no desempenho ao associar dados a um único objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com milhares de propriedades. Você pode minimizar esse impacto dividindo o objeto único em vários objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com menos propriedades. A tabela mostra os tempos de renderização e associação da vinculação de dados para um único objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] grande em comparação com vários objetos menores.  
  
|**Vinculação de dados de mil objetos TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para um objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com mil propriedades|950|1200|  
|Para mil objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com uma propriedade|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Associando a um ItemsSource  
 Considere um cenário em que você tenha um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto que contém uma lista de funcionários que você deseja exibir em um <xref:System.Windows.Controls.ListBox>. Para criar uma correspondência entre esses dois objetos, você deve vincular sua lista de funcionários para o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox>. No entanto, suponha que você tenha um novo funcionário ingressando em seu grupo. Você pode pensar que para inserir essa nova pessoa em seu limite <xref:System.Windows.Controls.ListBox> valores, você simplesmente adicionar esta pessoa à sua lista de funcionários e esperar que essa alteração seja reconhecida pelo mecanismo de associação de dados automaticamente. Essa suposição iria se provar falsa; Na realidade, a alteração não será refletida no <xref:System.Windows.Controls.ListBox> automaticamente. Isso ocorre porque o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto não gera automaticamente um evento de alteração de coleção. Para obter o <xref:System.Windows.Controls.ListBox> para acompanhar as alterações, você precisaria recriar sua lista de funcionários e reanexá-lo para o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox>. Embora essa solução funcione, ela ocasiona um grande impacto no desempenho. Sempre que você reatribuir o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.ListBox> para um novo objeto, o <xref:System.Windows.Controls.ListBox> primeiro joga fora de seus itens anteriores e regenera sua lista inteira. O impacto no desempenho é ampliado se sua <xref:System.Windows.Controls.ListBox> é mapeado para um complexo <xref:System.Windows.DataTemplate>.  
  
 Uma solução muito eficiente para esse problema é fazer o funcionário listar um <xref:System.Collections.ObjectModel.ObservableCollection%601>. Um <xref:System.Collections.ObjectModel.ObservableCollection%601> objeto gera uma notificação de alteração que o mecanismo de associação de dados pode receber. O evento adiciona ou remove um item de um <xref:System.Windows.Controls.ItemsControl> sem precisar gerar a lista inteira.  
  
 A tabela abaixo mostra o tempo necessário para atualizar o <xref:System.Windows.Controls.ListBox> (com virtualização de interface do usuário desativada) quando um item é adicionado. O número da primeira linha representa o tempo decorrido quando o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto está associado a <xref:System.Windows.Controls.ListBox> do elemento <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. O número na segunda linha representa o tempo decorrido quando uma <xref:System.Collections.ObjectModel.ObservableCollection%601> está associada ao <xref:System.Windows.Controls.ListBox> do elemento <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Observe que a economia de tempo significativo usando o <xref:System.Collections.ObjectModel.ObservableCollection%601> estratégia de associação de dados.  
  
|**Vinculação de dados de ItemsSource**|**Atualizar tempo para 1 item (ms)**|  
|--------------------------------------|---------------------------------------|  
|Para uma [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto|1656|  
|Para um <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Associar IList a ItemsControl não IEnumerable  
 Se você tem a opção de associar um <xref:System.Collections.Generic.IList%601> ou um <xref:System.Collections.IEnumerable> para um <xref:System.Windows.Controls.ItemsControl> de objeto, escolha o <xref:System.Collections.Generic.IList%601> objeto. Associação <xref:System.Collections.IEnumerable> para um <xref:System.Windows.Controls.ItemsControl> força [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para criar um wrapper <xref:System.Collections.Generic.IList%601> objeto, o que significa que o desempenho é afetado pela sobrecarga desnecessária de um segundo objeto.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Não converta objetos CLR em XML apenas para vinculação de dados.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite associar dados a conteúdo [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. No entanto, a vinculação de dados ao conteúdo [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] é mais lenta que a vinculação de dados a objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Não converta os dados de objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] em XML se o único objetivo for a vinculação de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planejando para desempenho do aplicativo](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Aproveitando o hardware](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportamento do objeto](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Recursos do aplicativo](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Outras recomendações de desempenho](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
