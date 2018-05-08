---
title: Como usar gatilhos para criar itens selecionados em um ListView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 1741ce84fab1639409a7c834845573239c51cc35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>Como usar gatilhos para criar itens selecionados em um ListView
Este exemplo mostra como definir <xref:System.Windows.Style.Triggers%2A> para um <xref:System.Windows.Controls.ListViewItem> controle para que quando um valor de propriedade de um <xref:System.Windows.Controls.ListViewItem> alterações, o <xref:System.Windows.Style> do <xref:System.Windows.Controls.ListViewItem> alterações na resposta.  
  
## <a name="example"></a>Exemplo  
 Se você quiser que o <xref:System.Windows.Style> de um <xref:System.Windows.Controls.ListViewItem> para alterar em resposta a alterações de propriedades, defina <xref:System.Windows.Style.Triggers%2A> para o <xref:System.Windows.Style> alterar.  
  
 O exemplo a seguir define uma <xref:System.Windows.Trigger> que define o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade <xref:System.Windows.Media.Brushes.Blue%2A> e altera o <xref:System.Windows.FrameworkElement.Cursor%2A> para exibir uma <xref:System.Windows.Input.CursorType.Hand> quando o <xref:System.Windows.UIElement.IsMouseOver%2A> alteração na propriedade `true`.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 O exemplo a seguir define uma <xref:System.Windows.MultiTrigger> que define o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade de um <xref:System.Windows.Controls.ListViewItem> para <xref:System.Windows.Media.Brushes.Yellow%2A> quando o <xref:System.Windows.Controls.ListViewItem> é o item selecionado e tem o foco do teclado.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
