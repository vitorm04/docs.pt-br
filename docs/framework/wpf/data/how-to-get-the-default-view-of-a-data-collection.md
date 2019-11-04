---
title: Como obter a exibição padrão de uma coleta de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459122"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Como obter a exibição padrão de uma coleta de dados
As exibições permitem que a mesma coleta de dados seja visualizada de diferentes maneiras, dependendo dos critérios de classificação, filtragem ou agrupamento. Cada coleta tem uma exibição padrão compartilhada, que é usada como a fonte de associação real quando uma associação especifica uma coleta como sua origem. Este exemplo mostra como conseguir a exibição padrão de uma coleta.  
  
## <a name="example"></a>Exemplo  
 Para criar a exibição, você precisa de uma referência de objeto para a coleta. Esse objeto de dados pode ser obtido referenciando seu próprio objeto code-behind, obtendo o contexto de dados, obtendo uma propriedade da fonte de dados ou obtendo uma propriedade da associação. Este exemplo mostra como obter a <xref:System.Windows.FrameworkElement.DataContext%2A> de um objeto de dados e usá-lo para obter diretamente o modo de exibição de coleção padrão para essa coleção.  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 Neste exemplo, o elemento raiz é um <xref:System.Windows.Controls.StackPanel>. O <xref:System.Windows.FrameworkElement.DataContext%2A> é definido como *Mydataname*, que se refere a um provedor de dados que é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de objetos *Order* .  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Como alternativa, você pode instanciar e associar ao seu próprio modo de exibição de coleção usando a classe <xref:System.Windows.Data.CollectionViewSource>. Essa exibição de coleta é compartilhada somente por controles que se associam a ela diretamente. Para um exemplo, consulte a seção Como Criar uma Exibição em [Visão geral de associação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
 Para obter exemplos da funcionalidade fornecida por uma exibição de coleta, consulte [Classificar dados em uma exibição](how-to-sort-data-in-a-view.md), [Filtrar dados em uma exibição](how-to-filter-data-in-a-view.md) e [Navegar pelos objetos em uma exibição de coleta de dados](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Consulte também

- [Classificar e agrupar dados usando uma exibição em XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
