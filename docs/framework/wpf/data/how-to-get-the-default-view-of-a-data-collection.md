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
ms.openlocfilehash: e8e6928391a98a132f1dbb39edfda0d73d2eebdb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557167"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Como obter a exibição padrão de uma coleta de dados
As exibições permitem que a mesma coleta de dados seja visualizada de diferentes maneiras, dependendo dos critérios de classificação, filtragem ou agrupamento. Cada coleta tem uma exibição padrão compartilhada, que é usada como a fonte de associação real quando uma associação especifica uma coleta como sua origem. Este exemplo mostra como conseguir a exibição padrão de uma coleta.  
  
## <a name="example"></a>Exemplo  
 Para criar a exibição, você precisa de uma referência de objeto para a coleta. Esse objeto de dados pode ser obtido referenciando seu próprio objeto code-behind, obtendo o contexto de dados, obtendo uma propriedade da fonte de dados ou obtendo uma propriedade da associação. Este exemplo mostra como obter o <xref:System.Windows.FrameworkElement.DataContext%2A> de um objeto de dados e use-lo diretamente para obter a coleção padrão exibir para esta coleção.  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 Neste exemplo, o elemento raiz é um <xref:System.Windows.Controls.StackPanel>. O <xref:System.Windows.FrameworkElement.DataContext%2A> é definido como *minhaFonteDeDados*, que se refere a um provedor de dados que é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de *ordem* objetos.  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Como alternativa, você pode criar uma instância e vincular a sua própria exibição de coleção usando o <xref:System.Windows.Data.CollectionViewSource> classe. Essa exibição de coleta é compartilhada somente por controles que se associam a ela diretamente. Para um exemplo, consulte a seção Como Criar uma Exibição em [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Para obter exemplos da funcionalidade fornecida por uma exibição de coleta, consulte [Classificar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filtrar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md) e [Navegar pelos objetos em uma exibição de coleta de dados](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Classificar e agrupar dados usando uma exibição em XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
