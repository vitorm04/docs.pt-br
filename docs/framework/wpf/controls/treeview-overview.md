---
title: Visão geral de TreeView
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 267e870e13d26439e4fbcbba3c5741ff84cabe3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187378"
---
# <a name="treeview-overview"></a>Visão geral de TreeView
O <xref:System.Windows.Controls.TreeView> controle fornece uma maneira de exibir informações em uma estrutura hierárquica usando nódulos dobráveis. Este tópico introduz <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.TreeViewItem> os controles e fornece exemplos simples de seu uso.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>O que é um TreeView?  
 <xref:System.Windows.Controls.TreeView>é <xref:System.Windows.Controls.ItemsControl> um que aninha os <xref:System.Windows.Controls.TreeViewItem> itens usando controles. O exemplo a <xref:System.Windows.Controls.TreeView>seguir cria um .  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>Criando um TreeView  
 O <xref:System.Windows.Controls.TreeView> controle contém uma <xref:System.Windows.Controls.TreeViewItem> hierarquia de controles. Um <xref:System.Windows.Controls.TreeViewItem> controle <xref:System.Windows.Controls.HeaderedItemsControl> é um <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> que <xref:System.Windows.Controls.ItemsControl.Items%2A> tem uma coleção.  
  
 Se você estiver <xref:System.Windows.Controls.TreeView> definindo um usando, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> você pode <xref:System.Windows.Controls.TreeViewItem> definir explicitamente o conteúdo de um controle e os itens que compõem sua coleção. A ilustração anterior demonstra esse método.  
  
 Você também pode <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> especificar uma fonte <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> de <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> dados <xref:System.Windows.Controls.TreeViewItem> e, em seguida, especificar um e definir o conteúdo.  
  
 Para definir o <xref:System.Windows.Controls.TreeViewItem> layout de um <xref:System.Windows.HierarchicalDataTemplate> controle, você também pode usar objetos. Para obter mais informações e um exemplo, consulte [Usar SelectedValue, SelectedValuePath e SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Se um item <xref:System.Windows.Controls.TreeViewItem> não for um controle, ele <xref:System.Windows.Controls.TreeViewItem> é <xref:System.Windows.Controls.TreeView> automaticamente fechado por um controle quando o controle é exibido.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Expandindo e Recolhendo um TreeViewItem  
 Se o usuário <xref:System.Windows.Controls.TreeViewItem>expandir <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> a, a `true`propriedade será definida como . Você também pode expandir <xref:System.Windows.Controls.TreeViewItem> ou colapsar um <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> sem qualquer ação direta do usuário, definindo a propriedade para `true` (expandir) ou `false` (colapso). Quando essa propriedade <xref:System.Windows.Controls.TreeViewItem.Expanded> muda, um evento ou <xref:System.Windows.Controls.TreeViewItem.Collapsed> evento ocorre.  
  
 Quando <xref:System.Windows.FrameworkElement.BringIntoView%2A> o método é <xref:System.Windows.Controls.TreeViewItem> chamado <xref:System.Windows.Controls.TreeViewItem> de controle, os controles e seus pais <xref:System.Windows.Controls.TreeViewItem> se expandem. Se <xref:System.Windows.Controls.TreeViewItem> a não for visível ou <xref:System.Windows.Controls.TreeView> parcialmente visível, os pergaminhos para torná-lo visível.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>Seleção de TreeViewItem  
 Quando um usuário <xref:System.Windows.Controls.TreeViewItem> clica em um <xref:System.Windows.Controls.TreeViewItem.Selected> controle para <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> selecioná-lo, o evento ocorre e sua propriedade é definida como `true`. O <xref:System.Windows.Controls.TreeViewItem> também <xref:System.Windows.Controls.TreeView.SelectedItem%2A> se <xref:System.Windows.Controls.TreeView> torna o do controle. Por outro lado, quando <xref:System.Windows.Controls.TreeViewItem> a seleção muda de um controle, seu <xref:System.Windows.Controls.TreeViewItem.Unselected> evento ocorre e sua <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> propriedade é definida como `false`.  
  
 A <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade <xref:System.Windows.Controls.TreeView> no controle é uma propriedade somente leitura; portanto, você não pode explicitamente defini-lo. A <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade é definida se o <xref:System.Windows.Controls.TreeViewItem> usuário clicar <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> em um `true` controle <xref:System.Windows.Controls.TreeViewItem> ou quando a propriedade estiver definida no controle.  
  
 Use <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> a propriedade <xref:System.Windows.Controls.TreeView.SelectedValue%2A> para <xref:System.Windows.Controls.TreeView.SelectedItem%2A>especificar um de a . Para obter mais informações, consulte [Usar SelectedValue, SelectedValuePath e SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Você pode registrar um <xref:System.Windows.Controls.TreeView.SelectedItemChanged> manipulador de eventos no <xref:System.Windows.Controls.TreeViewItem> evento para determinar quando um selecionado será alterado. O <xref:System.Windows.RoutedPropertyChangedEventArgs%601> que é fornecido ao manipulador <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>de eventos especifica o , <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>que é a seleção anterior, e o , que é a seleção atual. O valor poderá ser `null` se o aplicativo ou o usuário não tiver feito uma seleção anterior ou atual.  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>Estilo TreeView  
 O estilo padrão <xref:System.Windows.Controls.TreeView> de um controle <xref:System.Windows.Controls.StackPanel> coloca-o <xref:System.Windows.Controls.ScrollViewer> dentro de um objeto que contém um controle. Quando você <xref:System.Windows.FrameworkElement.Width%2A> define <xref:System.Windows.FrameworkElement.Height%2A> as <xref:System.Windows.Controls.TreeView>propriedades e propriedades para <xref:System.Windows.Controls.StackPanel> a, esses <xref:System.Windows.Controls.TreeView>valores são usados para dimensionar o objeto que exibe o . Se o conteúdo a ser exibido for <xref:System.Windows.Controls.ScrollViewer> maior que a área de exibição, um será exibido automaticamente para que o usuário possa rolar pelo <xref:System.Windows.Controls.TreeView> conteúdo.  
  
 Para personalizar a <xref:System.Windows.Controls.TreeViewItem> aparência de <xref:System.Windows.FrameworkElement.Style%2A> um controle, <xref:System.Windows.Style>defina a propriedade como um costume .  
  
 O exemplo a seguir <xref:System.Windows.Controls.Control.Foreground%2A> mostra <xref:System.Windows.Controls.Control.FontSize%2A> como definir <xref:System.Windows.Controls.TreeViewItem> os valores e propriedades para um controle usando um <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>Adicionando imagens e outros tipos de conteúdo aos itens do TreeView  
 Você pode incluir mais de <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> um <xref:System.Windows.Controls.TreeViewItem>objeto no conteúdo de um . Para incluir vários <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> objetos no conteúdo, inclua os objetos dentro de um controle de layout, como a <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.StackPanel>.  
  
 O exemplo a seguir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> mostra <xref:System.Windows.Controls.TreeViewItem> como <xref:System.Windows.Controls.CheckBox> definir <xref:System.Windows.Controls.TextBlock> o de a <xref:System.Windows.Controls.DockPanel> e que ambos estão fechados em um controle.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 O exemplo a seguir <xref:System.Windows.DataTemplate> mostra como <xref:System.Windows.Controls.Image> definir <xref:System.Windows.Controls.TextBlock> um que contém <xref:System.Windows.Controls.DockPanel> um e um que estão fechados em um controle. Você pode <xref:System.Windows.DataTemplate> usar um <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> para <xref:System.Windows.Controls.TreeViewItem>definir o ou para um .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Tópicos de como fazer](treeview-how-to-topics.md)
- [Modelo de conteúdo do WPF](wpf-content-model.md)
