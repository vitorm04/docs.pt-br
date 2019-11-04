---
title: Como associar um TreeView a dados que tenham uma profundidade indeterminável
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: cd9a1ee015ebb707a7a06d1c062a1bb3003c96e8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458620"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Como associar um TreeView a dados que tenham uma profundidade indeterminável
Pode haver ocasiões em que você deseja associar um <xref:System.Windows.Controls.TreeView> a uma fonte de dados cuja profundidade não é conhecida.  Isso pode ocorrer quando os dados são recursivos por natureza, como um sistema de arquivos, em que as pastas podem conter pastas, ou a estrutura organizacional da empresa, em que os funcionários têm outros funcionários como subordinados diretos.  
  
 A fonte de dados deve ter um modelo de objeto hierárquico. Por exemplo, uma classe `Employee` pode conter uma coleção de objetos Funcionários que são subordinados diretos de um funcionário. Se os dados forem representados de forma não hierárquica, será necessário compilar uma representação hierárquica dos dados.  
  
 Quando você define a propriedade <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> e se o <xref:System.Windows.Controls.ItemsControl> gera um <xref:System.Windows.Controls.ItemsControl> para cada item filho, o <xref:System.Windows.Controls.ItemsControl> filho usa o mesmo <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> que o pai. Por exemplo, se você definir a propriedade <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> em um <xref:System.Windows.Controls.TreeView>associado a dados, cada <xref:System.Windows.Controls.TreeViewItem> gerado usará a <xref:System.Windows.DataTemplate> que foi atribuída à propriedade <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> da <xref:System.Windows.Controls.TreeView>.  
  
 O <xref:System.Windows.HierarchicalDataTemplate> permite especificar o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para um <xref:System.Windows.Controls.TreeViewItem>ou qualquer <xref:System.Windows.Controls.HeaderedItemsControl>, no modelo de dados. Quando você define a propriedade <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType>, esse valor é usado quando a <xref:System.Windows.HierarchicalDataTemplate> é aplicada. Usando uma <xref:System.Windows.HierarchicalDataTemplate>, você pode definir recursivamente o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para cada <xref:System.Windows.Controls.TreeViewItem> no <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um <xref:System.Windows.Controls.TreeView> a dados hierárquicos e usar uma <xref:System.Windows.HierarchicalDataTemplate> para especificar a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para cada <xref:System.Windows.Controls.TreeViewItem>.  O <xref:System.Windows.Controls.TreeView> é associado a dados XML que representam os funcionários em uma empresa.  Cada elemento `Employee` pode conter outros elementos `Employee` para indicar quem responde a quem. Como os dados são recursivos, o <xref:System.Windows.HierarchicalDataTemplate> pode ser aplicado a cada nível.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral de modelagem dos dados](../data/data-templating-overview.md)
