---
title: Como usar o padrão de detalhes mestre com dados hierárquicos
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 46733b462861bdac3381cdacb8f2fbe0536d12eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Como usar o padrão de detalhes mestre com dados hierárquicos
Este exemplo mostra como implementar o cenário de detalhes mestre.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `LeagueList` é uma coleção de `Leagues`. Cada `League` tem um `Name` e uma coleção de `Divisions` e cada `Division` tem um nome e uma coleção de `Teams`. Cada `Team` tem um nome de equipe.  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Segue uma captura de tela do exemplo. O `Divisions` <xref:System.Windows.Controls.ListBox> automaticamente controla as seleções no `Leagues` <xref:System.Windows.Controls.ListBox> e exibir os dados correspondentes. O `Teams` <xref:System.Windows.Controls.ListBox> controla as seleções nos outros dois <xref:System.Windows.Controls.ListBox> controles.  
  
 ![Exemplo de detalhes mestre&#45](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 As duas coisas a se observar neste exemplo são:  
  
1.  Os três <xref:System.Windows.Controls.ListBox> controles vinculados à mesma fonte. Definir o <xref:System.Windows.Data.Binding.Path%2A> propriedade da associação para especificar qual nível de dados que você deseja o <xref:System.Windows.Controls.ListBox> para exibir.  
  
2.  Você deve definir o <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriedade `true` no <xref:System.Windows.Controls.ListBox> controles que a seleção que você está rastreando. A definição dessa propriedade garante que o item selecionado é sempre definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém seus dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza automaticamente seleção e moeda.  
  
 A técnica é um pouco diferente quando você usa dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Para ver um exemplo, confira [Usar o padrão de detalhes mestre com os dados XML hierárquicos](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Associar a uma coleção e exibir informações com base na seleção](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
