---
title: "Como associar um TreeView a dados que tenham uma profundidade indeterminável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be21ecb75420b6499e5b95d5f4d93a5f079f9646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Como associar um TreeView a dados que tenham uma profundidade indeterminável
Pode haver momentos em que você deseja associar um <xref:System.Windows.Controls.TreeView> para uma fonte de dados cuja profundidade não for conhecida.  Isso pode ocorrer quando os dados são recursivos por natureza, como um sistema de arquivos, em que as pastas podem conter pastas, ou a estrutura organizacional da empresa, em que os funcionários têm outros funcionários como subordinados diretos.  
  
 A fonte de dados deve ter um modelo de objeto hierárquico. Por exemplo, uma classe `Employee` pode conter uma coleção de objetos Funcionários que são subordinados diretos de um funcionário. Se os dados forem representados de forma não hierárquica, será necessário compilar uma representação hierárquica dos dados.  
  
 Quando você define o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> propriedade e se a <xref:System.Windows.Controls.ItemsControl> gera um <xref:System.Windows.Controls.ItemsControl> para cada item filho e, em seguida, o filho <xref:System.Windows.Controls.ItemsControl> usa a mesma <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> como pai. Por exemplo, se você definir o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade em uma associação de dados <xref:System.Windows.Controls.TreeView>, cada <xref:System.Windows.Controls.TreeViewItem> que é gerada usa o <xref:System.Windows.DataTemplate> que foi atribuído ao <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade o <xref:System.Windows.Controls.TreeView>.  
  
 O <xref:System.Windows.HierarchicalDataTemplate> permite que você especifique o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para um <xref:System.Windows.Controls.TreeViewItem>, ou qualquer <xref:System.Windows.Controls.HeaderedItemsControl>, no modelo de dados. Quando você define o <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> propriedade, que o valor é usado quando o <xref:System.Windows.HierarchicalDataTemplate> é aplicada. Usando um <xref:System.Windows.HierarchicalDataTemplate>, você pode definir recursivamente a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para cada <xref:System.Windows.Controls.TreeViewItem> no <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como vincular um <xref:System.Windows.Controls.TreeView> para dados hierárquicos e use um <xref:System.Windows.HierarchicalDataTemplate> para especificar o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para cada <xref:System.Windows.Controls.TreeViewItem>.  O <xref:System.Windows.Controls.TreeView> associa aos dados XML que representa os funcionários de uma empresa.  Cada elemento `Employee` pode conter outros elementos `Employee` para indicar quem responde a quem. Como os dados são recursivo, o <xref:System.Windows.HierarchicalDataTemplate> pode ser aplicado a cada nível.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)
