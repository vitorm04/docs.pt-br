---
title: 'Otimizando desempenho: vinculação de dados'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 3128f453378f9d74f867b571e30f2be4e8add8a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186755"
---
# <a name="optimizing-performance-data-binding"></a>Otimizando desempenho: vinculação de dados
A vinculação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece aos aplicativos uma maneira simples e consistente para apresentar e interagir com os dados. Os elementos podem ser vinculados a dados de uma variedade de fontes de dados na forma de objetos CLR e XML.  
  
 Este tópico apresenta recomendações de desempenho de vinculação de dados.  

<a name="HowDataBindingReferencesAreResolved"></a>
## <a name="how-data-binding-references-are-resolved"></a>Como as referências de vinculação de dados são resolvidas  
 Antes de discutir os problemas de desempenho da vinculação de dados, vale a pena explorar como o mecanismo de vinculação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] resolve referências de objeto para associação.  
  
 A fonte [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de uma vinculação de dados pode ser qualquer objeto CLR. Você pode vincular-se a propriedades, subpropriedades ou indexadores de um objeto CLR. As referências de vinculação são resolvidas usando <xref:System.ComponentModel.ICustomTypeDescriptor>a reflexão Microsoft .NET Framework ou uma . Aqui estão três métodos para resolver referências de objeto para associação.  
  
 O primeiro método envolve o uso de reflexão. Neste caso, <xref:System.Reflection.PropertyInfo> o objeto é usado para descobrir os atributos da propriedade e fornece acesso a metadados de propriedade. Ao usar <xref:System.ComponentModel.ICustomTypeDescriptor> a interface, o mecanismo de vinculação de dados usa essa interface para acessar os valores de propriedade. A <xref:System.ComponentModel.ICustomTypeDescriptor> interface é especialmente útil nos casos em que o objeto não possui um conjunto estático de propriedades.  
  
 As notificações de alteração de propriedade <xref:System.ComponentModel.INotifyPropertyChanged> podem ser fornecidas implementando a interface ou usando as notificações de alteração associadas ao <xref:System.ComponentModel.TypeDescriptor>. No entanto, a estratégia preferida para <xref:System.ComponentModel.INotifyPropertyChanged>implementar notificações de alteração de propriedade é usar .  
  
 Se o objeto de origem for um objeto CLR e [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a propriedade de origem for uma propriedade <xref:System.ComponentModel.TypeDescriptor>CLR, o mecanismo <xref:System.ComponentModel.PropertyDescriptor>de vinculação de dados terá que primeiro usar a reflexão sobre o objeto de origem para obter o e, em seguida, consultar para um . Essa sequência de operações de reflexão é potencialmente muito demorada de uma perspectiva de desempenho.  
  
 O segundo método para resolver referências de objetos envolve <xref:System.ComponentModel.INotifyPropertyChanged> um objeto de origem CLR que implementa a interface e uma propriedade de origem que é uma propriedade CLR. Nesse caso, o mecanismo de vinculação de dados usa reflexão diretamente no tipo de fonte e obtém a propriedade necessária. Este ainda não é o melhor método, mas ele custará menos nos requisitos de conjunto de trabalho do que o primeiro método.  
  
 O terceiro método para resolver referências de objetos envolve um objeto de origem que é uma <xref:System.Windows.DependencyObject> propriedade de origem que é um <xref:System.Windows.DependencyProperty>. Nesse caso, o mecanismo de vinculação de dados não precisa usar reflexão. Em vez disso, o mecanismo de propriedade e o mecanismo de vinculação de dados resolvem juntos a referência da propriedade independentemente. Esse é o melhor método para resolver referências de objeto usadas para vinculação de dados.  
  
 A tabela abaixo compara a <xref:System.Windows.Controls.TextBlock.Text%2A> velocidade dos <xref:System.Windows.Controls.TextBlock> dados que vinculam a propriedade de mil elementos usando esses três métodos.  
  
|**Associando a propriedade Text de um TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para uma propriedade de um objeto CLR|115|314|  
|Para uma propriedade de um objeto CLR que implementa<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|A <xref:System.Windows.DependencyProperty> um <xref:System.Windows.DependencyObject>de um.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>
## <a name="binding-to-large-clr-objects"></a>Associando a objetos CLR grandes  
 Há um impacto significativo no desempenho quando os dados se ligam a um único objeto CLR com milhares de propriedades. Você pode minimizar esse impacto dividindo o único objeto em vários objetos CLR com menos propriedades. A tabela mostra os tempos de vinculação e renderização para vinculação de dados a um único objeto CLR grande versus vários objetos menores.  
  
|**Vinculação de dados de mil objetos TextBlock**|**Tempo de associação (ms)**|**Tempo de renderização – inclui associação (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Para um objeto CLR com 1000 propriedades|950|1200|  
|Para 1000 objetos CLR com uma propriedade|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>
## <a name="binding-to-an-itemssource"></a>Associando a um ItemsSource  
 Considere um cenário no qual <xref:System.Collections.Generic.List%601> você tem um objeto CLR que contém <xref:System.Windows.Controls.ListBox>uma lista de funcionários que você deseja exibir em um . Para criar uma correspondência entre esses dois objetos, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> você <xref:System.Windows.Controls.ListBox>vincularia sua lista de funcionários à propriedade do . No entanto, suponha que você tenha um novo funcionário ingressando em seu grupo. Você pode pensar que, a fim de <xref:System.Windows.Controls.ListBox> inserir essa nova pessoa em seus valores vinculados, você simplesmente adicionar essa pessoa à sua lista de funcionários e esperar que essa mudança seja reconhecida automaticamente pelo mecanismo de vinculação de dados. Essa suposição provaria falsa; na realidade, a mudança não será <xref:System.Windows.Controls.ListBox> refletida automaticamente. Isso porque o <xref:System.Collections.Generic.List%601> objeto CLR não levanta automaticamente um evento alterado de coleção. Para obter a <xref:System.Windows.Controls.ListBox> coleta das alterações, você teria que recriar sua lista de <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> funcionários <xref:System.Windows.Controls.ListBox>e reanexá-la à propriedade do . Embora essa solução funcione, ela ocasiona um grande impacto no desempenho. Cada vez que você <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> reatribui o de <xref:System.Windows.Controls.ListBox> um novo objeto, o primeiro joga fora seus itens anteriores e regenera toda a sua lista. O impacto de desempenho <xref:System.Windows.Controls.ListBox> é ampliado <xref:System.Windows.DataTemplate>se seus mapas para um complexo .  
  
 Uma solução muito eficiente para este problema <xref:System.Collections.ObjectModel.ObservableCollection%601>é fazer com que sua lista de funcionários seja uma . Um <xref:System.Collections.ObjectModel.ObservableCollection%601> objeto levanta uma notificação de alteração que o mecanismo de vinculação de dados pode receber. O evento adiciona ou remove um <xref:System.Windows.Controls.ItemsControl> item de um sem a necessidade de regenerar toda a lista.  
  
 A tabela abaixo mostra o tempo <xref:System.Windows.Controls.ListBox> que leva para atualizar o (com a virtualização da ui desligada) quando um item é adicionado. O número na primeira linha representa o tempo decorrido quando o objeto CLR <xref:System.Collections.Generic.List%601> está vinculado ao <xref:System.Windows.Controls.ListBox> do <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>elemento . O número na segunda linha representa o tempo <xref:System.Collections.ObjectModel.ObservableCollection%601> decorrido <xref:System.Windows.Controls.ListBox> quando um <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>está vinculado ao do elemento . Observe a economia significativa <xref:System.Collections.ObjectModel.ObservableCollection%601> de tempo usando a estratégia de vinculação de dados.  
  
|**Vinculação de dados de ItemsSource**|**Atualizar tempo para 1 item (ms)**|  
|--------------------------------------|---------------------------------------|  
|Para um <xref:System.Collections.Generic.List%601> objeto CLR|1656|  
|Para um<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Associar IList a ItemsControl não IEnumerable  
 Se você tiver uma <xref:System.Collections.Generic.IList%601> escolha <xref:System.Collections.IEnumerable> entre <xref:System.Windows.Controls.ItemsControl> vincular um <xref:System.Collections.Generic.IList%601> ou um a um objeto, escolha o objeto. Vinculando-se <xref:System.Collections.IEnumerable> a uma <xref:System.Windows.Controls.ItemsControl> força [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para criar um objeto de invólucro, <xref:System.Collections.Generic.IList%601> o que significa que seu desempenho é impactado pela sobrecarga desnecessária de um segundo objeto.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Não converta objetos CLR em XML apenas para vinculação de dados.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]permite que os dados se vinculem ao conteúdo XML; no entanto, a vinculação de dados ao conteúdo XML é mais lenta do que a vinculação de dados a objetos CLR. Não converta dados de objeto CLR em XML se o único propósito for para vinculação de dados.  
  
## <a name="see-also"></a>Confira também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando o desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitar o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos de aplicação](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Passo a passo: Armazenando dados de aplicativo em cache em um aplicativo WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
