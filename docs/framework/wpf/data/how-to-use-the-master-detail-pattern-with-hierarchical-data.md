---
title: Como usar o padrão de detalhes mestre com dados hierárquicos
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e4183ddc3868a1568662853b46e05348df129092
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733474"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Como usar o padrão de detalhes mestre com dados hierárquicos
Este exemplo mostra como implementar o cenário de detalhes mestre.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `LeagueList` é uma coleção de `Leagues`. Cada `League` tem um `Name` e uma coleção de `Divisions` e cada `Division` tem um nome e uma coleção de `Teams`. Cada `Team` tem um nome de equipe.  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Segue uma captura de tela do exemplo. O `Divisions` <xref:System.Windows.Controls.ListBox> rastreia seleções automaticamente no `Leagues` <xref:System.Windows.Controls.ListBox> e exibe os dados correspondentes. O `Teams` <xref:System.Windows.Controls.ListBox> controla seleções nos outros dois controles de <xref:System.Windows.Controls.ListBox>.  
  
 ![Captura de tela que mostra&#45;um exemplo de cenário de detalhes mestre.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 As duas coisas a se observar neste exemplo são:  
  
1. Os três controles de <xref:System.Windows.Controls.ListBox> se associam à mesma fonte. Defina a propriedade <xref:System.Windows.Data.Binding.Path%2A> da Associação para especificar qual nível de dados você deseja que o <xref:System.Windows.Controls.ListBox> exiba.  
  
2. Você deve definir a propriedade <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> como `true` nos controles de <xref:System.Windows.Controls.ListBox> dos quais a seleção está acompanhando. Definir essa propriedade garante que o item selecionado sempre seja definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza a seleção e a moeda automaticamente.  
  
 A técnica é ligeiramente diferente quando você está usando dados XML. Para ver um exemplo, confira [Usar o padrão de detalhes mestre com os dados XML hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.HierarchicalDataTemplate>
- [Associar a uma coleção e exibir informações com base na seleção](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral de modelagem dos dados](data-templating-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
