---
title: 'Como: Usar o padrão de detalhes mestre com os dados hierárquicos'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e0bbb24b07fdc1c362e2be43d69d189defbc27a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931880"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Como: Usar o padrão de detalhes mestre com os dados hierárquicos
Este exemplo mostra como implementar o cenário de detalhes mestre.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `LeagueList` é uma coleção de `Leagues`. Cada `League` tem um `Name` e uma coleção de `Divisions` e cada `Division` tem um nome e uma coleção de `Teams`. Cada `Team` tem um nome de equipe.  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Segue uma captura de tela do exemplo. O `Divisions` <xref:System.Windows.Controls.ListBox> controla automaticamente as seleções na `Leagues` <xref:System.Windows.Controls.ListBox> e exibir os dados correspondentes. O `Teams` <xref:System.Windows.Controls.ListBox> controla as seleções nos outros dois <xref:System.Windows.Controls.ListBox> controles.  
  
 ![Captura de tela que mostra um mestre&#45;exemplo de cenário de detalhes.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 As duas coisas a se observar neste exemplo são:  
  
1. Os três <xref:System.Windows.Controls.ListBox> controles se ligam à mesma fonte. Defina as <xref:System.Windows.Data.Binding.Path%2A> propriedade da associação para especificar o nível de dados que você deseja o <xref:System.Windows.Controls.ListBox> para exibir.  
  
2. Você deve definir a <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriedade para `true` no <xref:System.Windows.Controls.ListBox> controles que a seleção estiver acompanhando. A definição dessa propriedade garante que o item selecionado é sempre definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém seus dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza a seleção e moeda automaticamente.  
  
 A técnica é um pouco diferente quando você usa dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Para ver um exemplo, confira [Usar o padrão de detalhes mestre com os dados XML hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.HierarchicalDataTemplate>
- [Associar a uma coleção e exibir informações com base na seleção](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Visão geral de modelagem dos dados](data-templating-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
