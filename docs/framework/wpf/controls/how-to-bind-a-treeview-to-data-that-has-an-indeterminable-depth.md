---
title: 'Como: Associar um TreeView a dados que tenham uma profundidade indeterminável'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: 702a86f049635423a31e554d205dcc3cf4aa799d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605361"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Como: Associar um TreeView a dados que tenham uma profundidade indeterminável
Pode haver momentos em que você deseja associar um <xref:System.Windows.Controls.TreeView> para uma fonte de dados cuja profundidade não é conhecida.  Isso pode ocorrer quando os dados são recursivos por natureza, como um sistema de arquivos, em que as pastas podem conter pastas, ou a estrutura organizacional da empresa, em que os funcionários têm outros funcionários como subordinados diretos.  
  
 A fonte de dados deve ter um modelo de objeto hierárquico. Por exemplo, uma classe `Employee` pode conter uma coleção de objetos Funcionários que são subordinados diretos de um funcionário. Se os dados forem representados de forma não hierárquica, será necessário compilar uma representação hierárquica dos dados.  
  
 Quando você define o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> propriedade e, se o <xref:System.Windows.Controls.ItemsControl> gera um <xref:System.Windows.Controls.ItemsControl> para cada item filho e, em seguida, o filho <xref:System.Windows.Controls.ItemsControl> usa o mesmo <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> como pai. Por exemplo, se você definir a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade em uma associação de dados <xref:System.Windows.Controls.TreeView>, cada <xref:System.Windows.Controls.TreeViewItem> que é gerada usa os <xref:System.Windows.DataTemplate> que foi atribuído ao <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade do <xref:System.Windows.Controls.TreeView>.  
  
 O <xref:System.Windows.HierarchicalDataTemplate> permite que você especifique o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para um <xref:System.Windows.Controls.TreeViewItem>, ou qualquer <xref:System.Windows.Controls.HeaderedItemsControl>, no modelo de dados. Quando você define o <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> propriedade, o que o valor é usado quando o <xref:System.Windows.HierarchicalDataTemplate> é aplicado. Usando um <xref:System.Windows.HierarchicalDataTemplate>, é possível definir recursivamente o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para cada <xref:System.Windows.Controls.TreeViewItem> no <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um <xref:System.Windows.Controls.TreeView> para dados hierárquicos e usar um <xref:System.Windows.HierarchicalDataTemplate> para especificar o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para cada <xref:System.Windows.Controls.TreeViewItem>.  O <xref:System.Windows.Controls.TreeView> se associa aos dados XML que representa os funcionários da empresa.  Cada elemento `Employee` pode conter outros elementos `Employee` para indicar quem responde a quem. Porque os dados são recursivos, o <xref:System.Windows.HierarchicalDataTemplate> pode ser aplicado a cada nível.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)
