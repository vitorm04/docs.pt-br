---
title: "Visão geral de TreeView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bf50346cc179a5aae860a7651d28e104bac3c2ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="treeview-overview"></a>Visão geral de TreeView
O <xref:System.Windows.Controls.TreeView> controle fornece uma maneira de exibir informações em uma estrutura hierárquica usando nós recolhíveis. Este tópico apresenta o <xref:System.Windows.Controls.TreeView> e <xref:System.Windows.Controls.TreeViewItem> controla e fornece exemplos simples de seu uso.  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>O que é um TreeView?  
 <xref:System.Windows.Controls.TreeView>é um <xref:System.Windows.Controls.ItemsControl> que aninha os itens usando <xref:System.Windows.Controls.TreeViewItem> controles. O exemplo a seguir cria um <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>Criando um TreeView  
 O <xref:System.Windows.Controls.TreeView> controle contém uma hierarquia de <xref:System.Windows.Controls.TreeViewItem> controles. Um <xref:System.Windows.Controls.TreeViewItem> controle é um <xref:System.Windows.Controls.HeaderedItemsControl> que tem um <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> e um <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção.  
  
 Se você estiver definindo um <xref:System.Windows.Controls.TreeView> usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode definir explicitamente o <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> conteúdo de um <xref:System.Windows.Controls.TreeViewItem> controle e os itens que compõem sua coleção. A ilustração anterior demonstra esse método.  
  
 Você também pode especificar um <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> como um tipo de dados de origem e, em seguida, especifique um <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> e <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> para definir o <xref:System.Windows.Controls.TreeViewItem> conteúdo.  
  
 Para definir o layout de um <xref:System.Windows.Controls.TreeViewItem> controle, você também pode usar <xref:System.Windows.HierarchicalDataTemplate> objetos. Para obter mais informações e um exemplo, consulte [Usar SelectedValue, SelectedValuePath e SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Se um item não é um <xref:System.Windows.Controls.TreeViewItem> controle, ele será automaticamente encapsulado por um <xref:System.Windows.Controls.TreeViewItem> controlar quando o <xref:System.Windows.Controls.TreeView> controle é exibido.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Expandindo e Recolhendo um TreeViewItem  
 Se o usuário expandir uma <xref:System.Windows.Controls.TreeViewItem>, o <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> está definida como `true`. Você também pode expandir ou recolher uma <xref:System.Windows.Controls.TreeViewItem> sem qualquer ação direta do usuário definindo o <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> propriedade `true` (expandir) ou `false` (Recolher). Quando essa propriedade for alterada, um <xref:System.Windows.Controls.TreeViewItem.Expanded> ou <xref:System.Windows.Controls.TreeViewItem.Collapsed> evento ocorre.  
  
 Quando o <xref:System.Windows.FrameworkElement.BringIntoView%2A> método for chamado em um <xref:System.Windows.Controls.TreeViewItem> controle, o <xref:System.Windows.Controls.TreeViewItem> e seu pai <xref:System.Windows.Controls.TreeViewItem> controles expandir. Se um <xref:System.Windows.Controls.TreeViewItem> não é visível ou parcialmente visível, o <xref:System.Windows.Controls.TreeView> rola para torná-lo visível.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>Seleção de TreeViewItem  
 Quando um usuário clica uma <xref:System.Windows.Controls.TreeViewItem> controle para selecioná-la, o <xref:System.Windows.Controls.TreeViewItem.Selected> evento ocorre e sua <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> está definida como `true`. O <xref:System.Windows.Controls.TreeViewItem> também se torna o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> do <xref:System.Windows.Controls.TreeView> controle. Por outro lado, quando a seleção é alterada de um <xref:System.Windows.Controls.TreeViewItem> controle, seu <xref:System.Windows.Controls.TreeViewItem.Unselected> evento ocorre e sua <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> está definida como `false`.  
  
 O <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade o <xref:System.Windows.Controls.TreeView> controle é uma propriedade somente leitura; Portanto, não é possível definir explicitamente. O <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade é definida se o usuário clica em um <xref:System.Windows.Controls.TreeViewItem> controle ou quando o <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> está definida como `true` no <xref:System.Windows.Controls.TreeViewItem> controle.  
  
 Use o <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedade para especificar um <xref:System.Windows.Controls.TreeView.SelectedValue%2A> de um <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Para obter mais informações, consulte [Usar SelectedValue, SelectedValuePath e SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Você pode registrar um manipulador de eventos no <xref:System.Windows.Controls.TreeView.SelectedItemChanged> evento para determinar quando um selecionado <xref:System.Windows.Controls.TreeViewItem> alterações. O <xref:System.Windows.RoutedPropertyChangedEventArgs%601> que é fornecido para o evento manipulador Especifica o <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, que é a seleção anterior e o <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, que é a seleção atual. O valor poderá ser `null` se o aplicativo ou o usuário não tiver feito uma seleção anterior ou atual.  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>Estilo TreeView  
 O estilo padrão de um <xref:System.Windows.Controls.TreeView> controle coloca dentro de um <xref:System.Windows.Controls.StackPanel> objeto que contém um <xref:System.Windows.Controls.ScrollViewer> controle. Quando você define o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades para um <xref:System.Windows.Controls.TreeView>, esses valores serão usados para dimensionar o <xref:System.Windows.Controls.StackPanel> objeto que exibe o <xref:System.Windows.Controls.TreeView>. Se a exibição de conteúdo é maior que a área de exibição, uma <xref:System.Windows.Controls.ScrollViewer> exibe automaticamente para que o usuário pode percorrer o <xref:System.Windows.Controls.TreeView> conteúdo.  
  
 Para personalizar a aparência de um <xref:System.Windows.Controls.TreeViewItem> controlar, defina o <xref:System.Windows.FrameworkElement.Style%2A> propriedade para um personalizado <xref:System.Windows.Style>.  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Controls.Control.Foreground%2A> e <xref:System.Windows.Controls.Control.FontSize%2A> valores de propriedades de um <xref:System.Windows.Controls.TreeViewItem> controle usando um <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Adicionando imagens e outros tipos de conteúdo aos itens do TreeView  
 Você pode incluir mais de um objeto no <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> conteúdo de um <xref:System.Windows.Controls.TreeViewItem>. Para incluir vários objetos em <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> conteúdo, coloque os objetos dentro de um controle de layout, como um <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.StackPanel>.  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> de um <xref:System.Windows.Controls.TreeViewItem> como um <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.TextBlock> que são colocados em um <xref:System.Windows.Controls.DockPanel> controle.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 O exemplo a seguir mostra como definir um <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.Image> e um <xref:System.Windows.Controls.TextBlock> que são colocados em um <xref:System.Windows.Controls.DockPanel> controle. Você pode usar um <xref:System.Windows.DataTemplate> para definir o <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> ou <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> para um <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Tópicos explicativos](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)  
 [Modelo de conteúdo do WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)
