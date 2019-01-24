---
title: 'Como: Alterar o alinhamento horizontal de uma coluna em um ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 07d5fd0830f98032e76b963cb32b35fd18b50475
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605218"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Como: Alterar o alinhamento horizontal de uma coluna em um ListView
Por padrão, o conteúdo de cada coluna em um <xref:System.Windows.Controls.ListViewItem> alinhado à esquerda. Você pode alterar o alinhamento de cada coluna, fornecendo uma <xref:System.Windows.DataTemplate> e definindo o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade no elemento dentro do <xref:System.Windows.DataTemplate>. Este tópico mostra como uma <xref:System.Windows.Controls.ListView> alinha seu conteúdo por padrão e como alterar o alinhamento de uma coluna em um <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, os dados nas colunas `Title` e `ISBN` são alinhados à esquerda.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Para alterar o alinhamento do `ISBN` coluna, você precisa especificar que o <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> propriedade de cada <xref:System.Windows.Controls.ListViewItem> é <xref:System.Windows.HorizontalAlignment.Stretch>, de modo que os elementos em cada <xref:System.Windows.Controls.ListViewItem> pode abranger ou ser posicionado ao longo de toda a largura de cada coluna. Porque o <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você precisará criar um estilo que define o <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Em seguida, você precisa usar um <xref:System.Windows.DataTemplate> para exibir o conteúdo em vez de usar o <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriedade. Para exibir o `ISBN` de cada modelo, o <xref:System.Windows.DataTemplate> pode conter apenas um <xref:System.Windows.Controls.TextBlock> que tem seu <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade definida como <xref:System.Windows.HorizontalAlignment.Right>.  
  
 O exemplo a seguir define o estilo e <xref:System.Windows.DataTemplate> necessárias para tornar o `ISBN` coluna alinhada à direita e as alterações a <xref:System.Windows.Controls.GridViewColumn> a referência a <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Associar dados XML usando um XMLDataProvider e consultas XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)
