---
title: 'Como: Classificar dados em uma exibição'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 50e1426f2a220c7d947f7feb9c3ec7e1c4de7643
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522668"
---
# <a name="how-to-sort-data-in-a-view"></a>Como: Classificar dados em uma exibição
Este exemplo descreve como classificar dados em uma exibição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um simples <xref:System.Windows.Controls.ListBox> e um <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 O <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos do botão contém a lógica para classificar os itens no <xref:System.Windows.Controls.ListBox> em ordem decrescente. Você pode fazer isso porque adicionar itens a um <xref:System.Windows.Controls.ListBox> dessa maneira adiciona ao <xref:System.Windows.Controls.ItemCollection> da <xref:System.Windows.Controls.ListBox>, e <xref:System.Windows.Controls.ItemCollection> deriva o <xref:System.Windows.Data.CollectionView> classe. Se você estiver associando sua <xref:System.Windows.Controls.ListBox> para uma coleção usando o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade, você pode usar a mesma técnica para classificar.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Desde que você tenha uma referência ao objeto de exibição, é possível usar a mesma técnica para classificar o conteúdo de outros modos de exibição de coleção. Para um exemplo de como obter uma exibição, consulte [Obter a exibição padrão de uma coleção de dados](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Para outro exemplo, consulte [Classificar uma coluna GridView quando um cabeçalho é clicado](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Para obter mais informações sobre modos de exibição, consulte associação a coleções em [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Para obter um exemplo de como aplicar a lógica de classificação em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], consulte [Classificar e agrupar dados usando um modo de exibição em XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [Classificar uma coluna GridView quando um cabeçalho é clicado](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Filtrar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
